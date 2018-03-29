---
title: Jak zarządzać globalne pakietów, pamięci podręcznej, folderów tymczasowych w NuGet | Dokumentacja firmy Microsoft
author: kraigb
ms.author: kraigb
manager: ghogen
ms.date: 03/19/2018
ms.topic: article
ms.prod: nuget
ms.technology: ''
description: Jak zarządzać folderu instalacji globalnej pakietu, pamięć podręczną pakietów i folderów tymczasowych, które istnieją na komputerze, które są używane podczas instalowania, przywracania i aktualizowanie pakietów.
keywords: Globalne dzaj pakietami folderu, pamięć podręczną pakietów NuGet, buforowanie pakietu, folder instalacji pakietu, pamięci podręcznych NuGet, zarządzanie pamięci podręcznych, lokalnej pamięci podręcznej NuGet, globalnej pamięci podręcznej NuGet, NuGet polecenie zmiennych lokalnych, czyszczenie pamięci podręcznej
ms.reviewer:
- karann-msft
- unniravindranathan
ms.openlocfilehash: e9f4383a3f1700b96e3d6fe9ea4c0a7c24daa45a
ms.sourcegitcommit: beb229893559824e8abd6ab16707fd5fe1c6ac26
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2018
---
# <a name="managing-the-global-packages-cache-and-temp-folders"></a><span data-ttu-id="63d50-104">Zarządzanie pakietów globalnej pamięci podręcznej i folderów tymczasowych</span><span class="sxs-lookup"><span data-stu-id="63d50-104">Managing the global packages, cache, and temp folders</span></span>

<span data-ttu-id="63d50-105">Zawsze, gdy zainstalować, zaktualizować lub przywracanie pakietu NuGet zarządza pakietów i informacji w kilku folderach poza struktury projektu:</span><span class="sxs-lookup"><span data-stu-id="63d50-105">Whenever you install, update, or restore a package, NuGet manages packages and package information in several folders outside of your project structure:</span></span>

| <span data-ttu-id="63d50-106">Nazwa</span><span class="sxs-lookup"><span data-stu-id="63d50-106">Name</span></span> | <span data-ttu-id="63d50-107">Opis i lokalizację (dla poszczególnych użytkowników)</span><span class="sxs-lookup"><span data-stu-id="63d50-107">Description and Location (per user)</span></span>|
| --- | --- |
| <span data-ttu-id="63d50-108">globalne&#8209;pakietów</span><span class="sxs-lookup"><span data-stu-id="63d50-108">global&#8209;packages</span></span> | <span data-ttu-id="63d50-109">*Globalne pakiety* jest folder, gdzie NuGet instaluje wszystkie pobranego pakietu.</span><span class="sxs-lookup"><span data-stu-id="63d50-109">The *global-packages* folder is where NuGet installs any downloaded package.</span></span> <span data-ttu-id="63d50-110">Każdy pakiet jest w pełni rozwinięta do podfolderu zgodny identyfikator pakietu i numer wersji.</span><span class="sxs-lookup"><span data-stu-id="63d50-110">Each package is fully expanded into a subfolder that matches the package identifier and version number.</span></span> <span data-ttu-id="63d50-111">Projektów przy użyciu PackageReference zawsze formatu Użyj pakietów bezpośrednio z tego folderu.</span><span class="sxs-lookup"><span data-stu-id="63d50-111">Projects using the PackageReference format always use packages directly from this folder.</span></span> <span data-ttu-id="63d50-112">Korzystając z `packages.config`, pakiety są instalowane na *globalne pakiety* folderu, następnie kopiowane do projektu `packages` folderu.</span><span class="sxs-lookup"><span data-stu-id="63d50-112">When using the `packages.config`, packages are installed to the *global-packages* folder, then copied into the project's `packages` folder.</span></span><br/><ul><li><span data-ttu-id="63d50-113">System Windows: `%userprofile%\.nuget\packages`</span><span class="sxs-lookup"><span data-stu-id="63d50-113">Windows: `%userprofile%\.nuget\packages`</span></span></li><li><span data-ttu-id="63d50-114">Mac/Linux: `~/.nuget/packages`</span><span class="sxs-lookup"><span data-stu-id="63d50-114">Mac/Linux: `~/.nuget/packages`</span></span></li><li><span data-ttu-id="63d50-115">Override, za pomocą zmiennej środowiskowej NUGET_PACKAGES, `globalPackagesFolder` lub `repositoryPath` [ustawienia konfiguracji](../reference/nuget-config-file.md#config-section) (przy użyciu PackageReference i `packages.config`odpowiednio), lub `RestorePackagesPath` MSBuild Właściwość (MSBuild tylko).</span><span class="sxs-lookup"><span data-stu-id="63d50-115">Override using the NUGET_PACKAGES environment variable, the `globalPackagesFolder` or `repositoryPath` [configuration settings](../reference/nuget-config-file.md#config-section) (when using PackageReference and `packages.config`, respectively), or the `RestorePackagesPath` MSBuild property (MSBuild only).</span></span> <span data-ttu-id="63d50-116">Zmienna środowiskowa mają pierwszeństwo przed ustawieniem konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="63d50-116">The environment variable takes precedence over the configuration setting.</span></span></li></ul> |
| <span data-ttu-id="63d50-117">http&#8209;cache</span><span class="sxs-lookup"><span data-stu-id="63d50-117">http&#8209;cache</span></span> | <span data-ttu-id="63d50-118">Menedżer pakietów programu Visual Studio (NuGet 3.x+) i `dotnet` narzędzia przechowują kopie pobrane pakiety w pamięci podręcznej (zapisane jako `.dat` plików), są organizowane w podfolderach dla każdego źródła pakietu.</span><span class="sxs-lookup"><span data-stu-id="63d50-118">The Visual Studio Package Manager (NuGet 3.x+) and the `dotnet` tool store copies of downloaded packages in this cache (saved as `.dat` files), organized into subfolders for each package source.</span></span> <span data-ttu-id="63d50-119">Pakiety nie zostaną rozwinięte, a pamięć podręczna zawiera czas wygaśnięcia 30 minut.</span><span class="sxs-lookup"><span data-stu-id="63d50-119">Packages are not expanded, and the cache has an expiration time of 30 minutes.</span></span><br/><ul><li><span data-ttu-id="63d50-120">System Windows: `%localappdata%\NuGet\v3-cache`</span><span class="sxs-lookup"><span data-stu-id="63d50-120">Windows: `%localappdata%\NuGet\v3-cache`</span></span></li><li><span data-ttu-id="63d50-121">Mac/Linux: `~/.local/share/NuGet/v3-cache`</span><span class="sxs-lookup"><span data-stu-id="63d50-121">Mac/Linux: `~/.local/share/NuGet/v3-cache`</span></span></li><li><span data-ttu-id="63d50-122">Override, za pomocą zmiennej środowiskowej NUGET_HTTP_CACHE_PATH.</span><span class="sxs-lookup"><span data-stu-id="63d50-122">Override using the NUGET_HTTP_CACHE_PATH environment variable.</span></span></li></ul> |
| <span data-ttu-id="63d50-123">Temp</span><span class="sxs-lookup"><span data-stu-id="63d50-123">temp</span></span> | <span data-ttu-id="63d50-124">Folder, w którym NuGet przechowuje pliki tymczasowe podczas jego różnych operacji.</span><span class="sxs-lookup"><span data-stu-id="63d50-124">A folder where NuGet stores temporary files during its various operations.</span></span><br/><li><span data-ttu-id="63d50-125">System Windows: `%temp%\NuGetScratch`</span><span class="sxs-lookup"><span data-stu-id="63d50-125">Windows: `%temp%\NuGetScratch`</span></span></li><li><span data-ttu-id="63d50-126">Mac/Linux: `/tmp/NuGetScratch`</span><span class="sxs-lookup"><span data-stu-id="63d50-126">Mac/Linux: `/tmp/NuGetScratch`</span></span></li></ul> |

> [!Note]
> <span data-ttu-id="63d50-127">NuGet 3.5 i wcześniejszych zastosowań *pamięci podręcznej pakiety* zamiast *pamięci podręcznej http*, który znajduje się w `%localappdata%\NuGet\Cache`.</span><span class="sxs-lookup"><span data-stu-id="63d50-127">NuGet 3.5 and earlier uses *packages-cache* instead of the *http-cache*, which is located in `%localappdata%\NuGet\Cache`.</span></span>

<span data-ttu-id="63d50-128">Przy użyciu pamięci podręcznej i *globalne pakiety* folderów, NuGet zazwyczaj pozwala uniknąć pobierania pakietów, które już istnieją na komputerze, poprawa wydajności instalacji, aktualizacji i operacji przywracania.</span><span class="sxs-lookup"><span data-stu-id="63d50-128">By using the cache and *global-packages* folders, NuGet generally avoids downloading packages that already exist on the computer, improving the performance of install, update, and restore operations.</span></span> <span data-ttu-id="63d50-129">Korzystając z PackageReference, *globalne pakiety* folderu również pozwala uniknąć porządkowania pobrane pakiety w folderach projektu, w których one mogą przypadkowo dodane do kontroli źródła i zmniejsza NuGet ogólnego wpływu na komputerze Magazyn.</span><span class="sxs-lookup"><span data-stu-id="63d50-129">When using PackageReference, the *global-packages* folder also avoids keeping downloaded packages inside project folders, where they might be inadvertently added to source control, and reduces NuGet's overall impact on computer storage.</span></span>

<span data-ttu-id="63d50-130">Po otrzymaniu monitu, aby pobrać pakiet, NuGet najpierw wyszukiwana *globalne pakiety* folderu.</span><span class="sxs-lookup"><span data-stu-id="63d50-130">When asked to retrieve a package, NuGet first looks in the *global-packages* folder.</span></span> <span data-ttu-id="63d50-131">Jeśli dokładną wersję pakietu nie jest dostępne, NuGet sprawdza wszystkie źródła pakietów w innych niż HTTP.</span><span class="sxs-lookup"><span data-stu-id="63d50-131">If the exact version of package is not there, then NuGet checks all non-HTTP package sources.</span></span> <span data-ttu-id="63d50-132">Jeśli nadal nie można znaleźć pakietu, NuGet szuka pakietu w *pamięci podręcznej http* chyba że zostanie `--no-cache` z `dotnet.exe` polecenia lub `-NoCache` z `nuget.exe` poleceń.</span><span class="sxs-lookup"><span data-stu-id="63d50-132">If the package is still not found, NuGet looks for the package in the *http-cache* unless you specify `--no-cache` with `dotnet.exe` commands or `-NoCache` with `nuget.exe` commands.</span></span> <span data-ttu-id="63d50-133">Jeśli pakiet nie znajduje się w pamięci podręcznej lub pamięci podręcznej nie jest używany, NuGet następnie pobiera pakiet za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="63d50-133">If the package is not in the cache, or the cache isn't used, NuGet then retrieves the package over HTTP .</span></span>

<span data-ttu-id="63d50-134">Aby uzyskać więcej informacji, zobacz [co się dzieje, gdy jest zainstalowany pakiet](ways-to-install-a-package.md#what-happens-when-a-package-is-installed).</span><span class="sxs-lookup"><span data-stu-id="63d50-134">For more information, see [What happens when a package is installed](ways-to-install-a-package.md#what-happens-when-a-package-is-installed).</span></span>

## <a name="viewing-folder-locations"></a><span data-ttu-id="63d50-135">Wyświetlanie lokalizacje folderów</span><span class="sxs-lookup"><span data-stu-id="63d50-135">Viewing folder locations</span></span>

<span data-ttu-id="63d50-136">Można wyświetlić przy użyciu lokalizacji folderu [polecenia zmiennych lokalnych nuget dotnet](/dotnet/core/tools/dotnet-nuget-locals):</span><span class="sxs-lookup"><span data-stu-id="63d50-136">You can view folder locations using the [dotnet nuget locals command](/dotnet/core/tools/dotnet-nuget-locals):</span></span>

```cli
dotnet nuget locals all --list
```

<span data-ttu-id="63d50-137">Dane wyjściowe zazwyczaj (system Mac/Linux; Nazwa bieżącego użytkownika jest "uzytkownik1"):</span><span class="sxs-lookup"><span data-stu-id="63d50-137">Typical output (Mac/Linux; "user1" is the current username):</span></span>

```output
info : http-cache: /home/user1/.local/share/NuGet/v3-cache
info : global-packages: /home/user1/.nuget/packages/
info : temp: /tmp/NuGetScratch
```

<span data-ttu-id="63d50-138">Aby wyświetlić lokalizacji folderu, użyj `http-cache`, `global-packages`, lub `temp` zamiast `all`.</span><span class="sxs-lookup"><span data-stu-id="63d50-138">To display the location of a single folder, use `http-cache`, `global-packages`, or `temp` instead of `all`.</span></span> 

<span data-ttu-id="63d50-139">Możesz również wyświetlić przy użyciu lokalizacji [polecenia nuget zmiennych lokalnych](../tools/cli-ref-locals.md):</span><span class="sxs-lookup"><span data-stu-id="63d50-139">You also view locations using the [nuget locals command](../tools/cli-ref-locals.md):</span></span>

```cli
# Display locals for all folders: global-packages, cache, and temp
nuget locals all -list
```

<span data-ttu-id="63d50-140">Dane wyjściowe zazwyczaj (z systemem Windows; Nazwa bieżącego użytkownika jest "uzytkownik1"):</span><span class="sxs-lookup"><span data-stu-id="63d50-140">Typical output (Windows; "user1" is the current username):</span></span>

```output
http-cache: C:\Users\user1\AppData\Local\NuGet\v3-cache
global-packages: C:\Users\user1\.nuget\packages\
temp: C:\Users\user1\AppData\Local\Temp\NuGetScratch
```

<span data-ttu-id="63d50-141">(`package-cache` jest używany w NuGet 2.x i pojawi się z NuGet 3.5 lub starszej.)</span><span class="sxs-lookup"><span data-stu-id="63d50-141">(`package-cache` is used in NuGet 2.x and appears with NuGet 3.5 and earlier.)</span></span>

## <a name="clearing-local-folders"></a><span data-ttu-id="63d50-142">Wyczyszczenie foldery lokalne</span><span class="sxs-lookup"><span data-stu-id="63d50-142">Clearing local folders</span></span>

<span data-ttu-id="63d50-143">Jeśli występują problemy z instalacją pakietu lub w przeciwnym razie chcesz zapewnić instalowany pakiety ze zdalnego galerii, użyj `locals --clear` opcji (dotnet.exe) lub `locals -clear` (nuget.exe), określenia folderu, aby wyczyścić, lub `all` do Usuń zaznaczenie wszystkich folderów:</span><span class="sxs-lookup"><span data-stu-id="63d50-143">If you encounter package installation problems or otherwise want to ensure that you're installing packages from a remote gallery, use the `locals --clear` option (dotnet.exe) or `locals -clear` (nuget.exe), specifying the folder to clear, or `all` to clear all folders:</span></span>

```cli
# Clear the 3.x+ cache (use either command)
dotnet nuget locals http-cache --clear
nuget locals http-cache -clear

# Clear the 2.x cache (NuGet CLI 3.5 and earlier only)
nuget locals packages-cache -clear

# Clear the global packages folder (use either command)
dotnet nuget locals global-packages --clear
nuget locals global-packages -clear

# Clear the temporary cache (use either command)
dotnet nuget locals temp --clear
nuget locals temp -clear

# Clear all caches (use either command)
dotnet nuget locals all --clear
nuget locals all -clear
```

<span data-ttu-id="63d50-144">Wszystkie pakiety używane w projektach, które są aktualnie otwarte w programie Visual Studio nie są usuwane z *globalne pakiety* folderu.</span><span class="sxs-lookup"><span data-stu-id="63d50-144">Any packages used by projects that are currently open in Visual Studio are not cleared from the *global-packages* folder.</span></span>

<span data-ttu-id="63d50-145">W programie Visual Studio, użyj **Narzędzia > Menedżera pakietów NuGet > Ustawienia Menedżera pakietów** menu polecenie, a następnie wybierz **wyczyść wszystkie Cache(s) NuGet**.</span><span class="sxs-lookup"><span data-stu-id="63d50-145">In Visual Studio, use the **Tools > NuGet Package Manager > Package Manager Settings** menu command, then select **Clear All NuGet Cache(s)**.</span></span> <span data-ttu-id="63d50-146">Zarządzanie pamięcią podręczną nie jest obecnie dostępna za pośrednictwem konsoli Menedżera pakietów.</span><span class="sxs-lookup"><span data-stu-id="63d50-146">Managing the cache isn't presently available through the Package Manager Console.</span></span>

![Polecenia NuGet opcję czyszczenia pamięci podręcznych](media/options-clear-caches.png)

## <a name="troubleshooting-errors"></a><span data-ttu-id="63d50-148">Rozwiązywanie problemów z błędami</span><span class="sxs-lookup"><span data-stu-id="63d50-148">Troubleshooting errors</span></span>

<span data-ttu-id="63d50-149">Następujące błędy może wystąpić, gdy za pomocą `nuget locals` lub `dotnet nuget locals`:</span><span class="sxs-lookup"><span data-stu-id="63d50-149">The following errors can occur when using `nuget locals` or `dotnet nuget locals`:</span></span>

- <span data-ttu-id="63d50-150">*Błąd: Proces nie może uzyskać dostępu do pliku <package> , ponieważ jest on używany przez inny proces* lub *wyczyszczenie zasobów lokalnych nie powiodło się: nie można usunąć jednego lub więcej plików*</span><span class="sxs-lookup"><span data-stu-id="63d50-150">*Error: The process cannot access the file <package> because it is being used by another process* or *Clearing local resources failed: Unable to delete one or more files*</span></span>

    <span data-ttu-id="63d50-151">Jeden lub więcej plików w folderze są używane przez inny proces; na przykład projektu programu Visual Studio jest otwarty, która odwołuje się do pakietów w *globalne pakiety* folderu.</span><span class="sxs-lookup"><span data-stu-id="63d50-151">One or more files in the folder are in use by another process; for example, a Visual Studio project is open that refers to packages in the *global-packages* folder.</span></span> <span data-ttu-id="63d50-152">Zamknij tych procesów i spróbuj ponownie.</span><span class="sxs-lookup"><span data-stu-id="63d50-152">Close those processes and try again.</span></span>

- <span data-ttu-id="63d50-153">*Błąd: Dostęp do ścieżki <path> odmowa* lub *katalog nie jest pusty*</span><span class="sxs-lookup"><span data-stu-id="63d50-153">*Error: Access to the path <path> is denied* or *The directory is not empty*</span></span>

    <span data-ttu-id="63d50-154">Nie masz uprawnień do usuwania plików w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="63d50-154">You don't have permission to delete files in the cache.</span></span> <span data-ttu-id="63d50-155">Zmień uprawnienia do folderu, jeśli to możliwe i spróbuj ponownie.</span><span class="sxs-lookup"><span data-stu-id="63d50-155">Change the folder permissions, if possible, and try again.</span></span> <span data-ttu-id="63d50-156">W przeciwnym razie skontaktuj się z administratorem systemu.</span><span class="sxs-lookup"><span data-stu-id="63d50-156">Otherwise, contact your system administrator.</span></span>

- <span data-ttu-id="63d50-157">*Błąd: Określona ścieżka i nazwa pliku jest zbyt długa. W pełni kwalifikowanej nazwy pliku musi być mniejsza niż 260 znaków, a nazwa katalogu musi być mniejsza niż 248 znaków.*</span><span class="sxs-lookup"><span data-stu-id="63d50-157">*Error: The specified path, file name, or both are too long. The fully qualified file name must be less than 260 characters, and the directory name must be less than 248 characters.*</span></span>

    <span data-ttu-id="63d50-158">Skróć nazwę folderu i spróbuj ponownie.</span><span class="sxs-lookup"><span data-stu-id="63d50-158">Shorten the folder names and try again.</span></span>