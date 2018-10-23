---
title: Informacje o wersji RTM 4,8 NuGet
description: Informacje o wersji programu NuGet 4.8.1 tym — znane problemy, poprawki, funkcje dodane i DCRs.
author: karann-msft
ms.author: karann
ms.date: 5/14/2018
ms.topic: conceptual
ms.openlocfilehash: d23c4a8874d3d2e1a9ea721c66b15bb458de88a3
ms.sourcegitcommit: 47858da1103848cc1b15bdc00ac7219c0ee4a6a0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44516246"
---
# <a name="nuget-48-rtm-release-notes"></a><span data-ttu-id="b4858-103">Informacje o wersji RTM 4,8 NuGet</span><span class="sxs-lookup"><span data-stu-id="b4858-103">NuGet 4.8 RTM Release Notes</span></span>

<span data-ttu-id="b4858-104">[Visual Studio 2017 15.8 RTW](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes) pochodzi z funkcjonalnością NuGet 4.8.</span><span class="sxs-lookup"><span data-stu-id="b4858-104">[Visual Studio 2017 15.8 RTW](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes) comes with NuGet 4.8 functionality.</span></span>

<span data-ttu-id="b4858-105">Dostępne są wersje wiersza polecenia funkcji:</span><span class="sxs-lookup"><span data-stu-id="b4858-105">Command line versions of the same functionality are also available:</span></span>
* <span data-ttu-id="b4858-106">4.8 - NuGet.exe [nuget.org/downloads](https://nuget.org/downloads)</span><span class="sxs-lookup"><span data-stu-id="b4858-106">NuGet.exe 4.8 - [nuget.org/downloads](https://nuget.org/downloads)</span></span>
* <span data-ttu-id="b4858-107">DotNet.exe - [platformy .NET Core SDK 2.1.400](https://www.microsoft.com/net/download/visual-studio-sdks)</span><span class="sxs-lookup"><span data-stu-id="b4858-107">DotNet.exe - [.NET Core SDK 2.1.400](https://www.microsoft.com/net/download/visual-studio-sdks)</span></span>


## <a name="summary-whats-new-in-this-release"></a><span data-ttu-id="b4858-108">Podsumowanie: nowości w tej wersji</span><span class="sxs-lookup"><span data-stu-id="b4858-108">Summary: What's New in this Release</span></span>
* <span data-ttu-id="b4858-109">NuGet.exe obsługuje teraz longfilenames w systemie Windows 10 — [#6937](https://github.com/NuGet/Home/issues/6937)</span><span class="sxs-lookup"><span data-stu-id="b4858-109">NuGet.exe now supports longfilenames on Windows 10 - [#6937](https://github.com/NuGet/Home/issues/6937)</span></span>
* <span data-ttu-id="b4858-110">Wtyczki uwierzytelniania działa teraz w MsBuild, DotNet.exe, NuGet.exe i Visual Studio, w tym dla wielu platform.</span><span class="sxs-lookup"><span data-stu-id="b4858-110">Authenication plugins now work across MsBuild, DotNet.exe, NuGet.exe and Visual Studio, including cross platform.</span></span> <span data-ttu-id="b4858-111">Pierwsza generacja wtyczki uwierzytelniania nie są obsługiwane w programie MsBuild DotNet.exe.</span><span class="sxs-lookup"><span data-stu-id="b4858-111">The first generation of authentication plugins were not supported in MsBuild, DotNet.exe.</span></span> <span data-ttu-id="b4858-112">Uwaga: (Wersja zapoznawcza) w programie VS 2017 15.9 kompilacje mają wtyczka uwierzytelniania usługi VSTS uwzględnione.</span><span class="sxs-lookup"><span data-stu-id="b4858-112">Note: VS 2017 15.9 Preview builds have a VSTS authentication plugin included.</span></span> [<span data-ttu-id="b4858-113">#6486</span><span class="sxs-lookup"><span data-stu-id="b4858-113">#6486</span></span>](https://github.com/NuGet/Home/issues/6486)
* <span data-ttu-id="b4858-114">Mechanizm rozpoznawania zestawu SDK w MsBuild teraz kompilacji w ramach pakietu nuget i instaluje się za pomocą narzędzi NuGet dla programu VS.</span><span class="sxs-lookup"><span data-stu-id="b4858-114">MsBuild's SDK Resolver now builds as part of NuGet and installs with NuGet tools for VS.</span></span> <span data-ttu-id="b4858-115">Należy unikać wersje wprowadzenie limitu synchronizacji. [#6799](https://github.com/NuGet/Home/issues/6799)</span><span class="sxs-lookup"><span data-stu-id="b4858-115">This will avoid versions getting out sync. [#6799](https://github.com/NuGet/Home/issues/6799)</span></span>
* <span data-ttu-id="b4858-116">PackageReference obsługuje teraz metadane DevelopmentDependency — [#4125](https://github.com/NuGet/Home/issues/4125)</span><span class="sxs-lookup"><span data-stu-id="b4858-116">PackageReference now supports DevelopmentDependency metadata - [#4125](https://github.com/NuGet/Home/issues/4125)</span></span>

## <a name="known-issues"></a><span data-ttu-id="b4858-117">Znane problemy</span><span class="sxs-lookup"><span data-stu-id="b4858-117">Known issues</span></span>
### <a name="installing-signed-packages-on-a-ci-machine-or-in-an-offline-environment-takes-longer-than-usual"></a><span data-ttu-id="b4858-118">Instalowanie pakietów podpisem, na komputerze ciągłą Integrację lub w trybie offline środowiska trwa dłużej niż zwykle</span><span class="sxs-lookup"><span data-stu-id="b4858-118">Installing signed packages on a CI machine or in an offline environment takes longer than usual</span></span>

#### <a name="issue"></a><span data-ttu-id="b4858-119">Problem</span><span class="sxs-lookup"><span data-stu-id="b4858-119">Issue</span></span>
<span data-ttu-id="b4858-120">Maszyny ma ograniczony dostęp do Internetu (na przykład maszynę kompilacji w przypadku ciągłej integracji/ciągłego Dostarczania), instalowania/Przywracanie pakietów nuget podpisem spowoduje ostrzeżenia ([NU3028](https://docs.microsoft.com/en-us/nuget/reference/errors-and-warnings/nu3028)) od czasu serwery odwołań są niedostępne.</span><span class="sxs-lookup"><span data-stu-id="b4858-120">If the machine has restricted internet access (such as a build machine in a CI/CD scenario), installing/restoring a signed nuget package will result a warning ([NU3028](https://docs.microsoft.com/en-us/nuget/reference/errors-and-warnings/nu3028)) since the revocation servers are not reachable.</span></span> <span data-ttu-id="b4858-121">To normalne zachowanie.</span><span class="sxs-lookup"><span data-stu-id="b4858-121">This is expected.</span></span> <span data-ttu-id="b4858-122">Jednak w niektórych przypadkach może to mieć niezamierzone concequences, takich jak pakiet instalacji/przywracania trwa dłużej niż zwykle.</span><span class="sxs-lookup"><span data-stu-id="b4858-122">However, in some cases, this may have unintended concequences such as the package install/restore taking longer than usual.</span></span>

#### <a name="workaround"></a><span data-ttu-id="b4858-123">Obejście</span><span class="sxs-lookup"><span data-stu-id="b4858-123">Workaround</span></span>
<span data-ttu-id="b4858-124">Aktualizowanie programu Visual Studio, 15.8.4 i NuGet.exe 4.8.1, w którym wprowadzono zmiennej środowiskowej, aby przełączyć tryb wyboru odwołania.</span><span class="sxs-lookup"><span data-stu-id="b4858-124">Update to Visual Studio 15.8.4 and NuGet.exe 4.8.1 where we introduced an environment variable to switch the revocation check mode.</span></span>
<span data-ttu-id="b4858-125">Ustawienie `NUGET_CERT_REVOCATION_MODE` zmiennej środowiskowej, aby `offline` wymusi pakietu NuGet, aby sprawdzić stanu odwołania certyfikatu wyłącznie w odniesieniu do listy odwołania certyfikatów z pamięci podręcznej, a nie próbuje skontaktować się z serwerami odwołań NuGet.</span><span class="sxs-lookup"><span data-stu-id="b4858-125">Setting the `NUGET_CERT_REVOCATION_MODE` environment variable to `offline` will force NuGet to check the revocation status of the certificate only against the cached certificate revocation list, and NuGet will not attempt to reach revocation servers.</span></span> <span data-ttu-id="b4858-126">Gdy tryb wyboru odwołania jest ustawiony na `offline`, ostrzeżenie będzie można zmienić na starszą wersję informacji.</span><span class="sxs-lookup"><span data-stu-id="b4858-126">When the revocation check mode is set to `offline`, the warning will be downgraded to an info.</span></span>

> [!Warning]
> <span data-ttu-id="b4858-127">Przełącz tryb wyboru odwołania do trybu offline w ramach normalnych okoliczności jest niezalecane.</span><span class="sxs-lookup"><span data-stu-id="b4858-127">It is not recommended to switch the revocation check mode to offline under normal cirumstances.</span></span> <span data-ttu-id="b4858-128">To spowoduje, że rozszerzenie NuGet, aby pominąć sprawdzanie odwołań w trybie online i wykonywać tylko w trybie offline odwołania sprawdzenie listy odwołania certyfikatów pamięci podręcznej, które mogą być nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="b4858-128">Doing so will cause NuGet to skip online revocation check and perform only an offline revocation check against the cached certificate revocation list which may be out of date.</span></span> <span data-ttu-id="b4858-129">To oznacza, że pakiety, gdzie certyfikat podpisywania został odwołany, będzie nadal zainstalowany/przywrócona, które w przeciwnym wypadku nie powiodłoby się sprawdzanie odwołań i nie będzie został zainstalowany.</span><span class="sxs-lookup"><span data-stu-id="b4858-129">This means packages where the signing certificate may have been revoked, will continue to be installed/restored, which otherwise would have failed revocation check and would not have been installed.</span></span>

### <a name="the-migrate-packagesconfig-to-packagereference-option-is-not-available-in-the-right-click-context-menu"></a><span data-ttu-id="b4858-130">`Migrate packages.config to PackageReference...` Opcja nie jest dostępna w menu kontekstowym kliknij prawym przyciskiem myszy</span><span class="sxs-lookup"><span data-stu-id="b4858-130">The `Migrate packages.config to PackageReference...` option is not available in the right-click context menu</span></span>

#### <a name="issue"></a><span data-ttu-id="b4858-131">Problem</span><span class="sxs-lookup"><span data-stu-id="b4858-131">Issue</span></span>

<span data-ttu-id="b4858-132">Przy pierwszym otwarciu projektu, NuGet może nie mieć zainicjowany, dopóki nie jest wykonywana operacja NuGet.</span><span class="sxs-lookup"><span data-stu-id="b4858-132">When a project is first opened, NuGet may not have initialized until a NuGet operation is performed.</span></span> <span data-ttu-id="b4858-133">Powoduje to możliwość migracji nie pojawiają się w menu kontekstowym kliknij prawym przyciskiem myszy na `packages.config` lub `References`.</span><span class="sxs-lookup"><span data-stu-id="b4858-133">This causes the migration option to not show up in the right-click context menu on `packages.config` or `References`.</span></span>

#### <a name="workaround"></a><span data-ttu-id="b4858-134">Obejście</span><span class="sxs-lookup"><span data-stu-id="b4858-134">Workaround</span></span>

<span data-ttu-id="b4858-135">Wykonaj jeden z następujących akcji NuGet:</span><span class="sxs-lookup"><span data-stu-id="b4858-135">Perform any one of the following NuGet actions:</span></span>
* <span data-ttu-id="b4858-136">Otwórz interfejs użytkownika Menedżera pakietów — kliknij prawym przyciskiem myszy `References` i wybierz pozycję `Manage NuGet Packages...`</span><span class="sxs-lookup"><span data-stu-id="b4858-136">Open the Package Manager UI - Right-click on `References` and select `Manage NuGet Packages...`</span></span>
* <span data-ttu-id="b4858-137">Otwórz konsolę Menedżera pakietów — z `Tools > NuGet Package Manager`, wybierz opcję `Package Manager Console`</span><span class="sxs-lookup"><span data-stu-id="b4858-137">Open the Package Manager Console - From `Tools > NuGet Package Manager`, select `Package Manager Console`</span></span>
* <span data-ttu-id="b4858-138">Uruchom Przywracanie pakietów NuGet — kliknij prawym przyciskiem myszy na węzeł rozwiązania w Eksploratorze rozwiązań i wybierz pozycję `Restore NuGet Packages`</span><span class="sxs-lookup"><span data-stu-id="b4858-138">Run NuGet restore - Right-click on the solution node in the Solution Explorer and select `Restore NuGet Packages`</span></span>
* <span data-ttu-id="b4858-139">Skompiluj projekt, który wyzwala również Przywracanie pakietów NuGet</span><span class="sxs-lookup"><span data-stu-id="b4858-139">Build the project which also triggers NuGet restore</span></span>

<span data-ttu-id="b4858-140">Teraz można wyświetlić opcji migracji.</span><span class="sxs-lookup"><span data-stu-id="b4858-140">You should now be able to see the migration option.</span></span> <span data-ttu-id="b4858-141">Należy zauważyć, że ta opcja nie jest obsługiwane i nie będzie widoczna dla typów projektów platformy ASP.NET i C++.</span><span class="sxs-lookup"><span data-stu-id="b4858-141">Note that this option is not supported and will not show up for ASP.NET and C++ project types.</span></span>
<span data-ttu-id="b4858-142">Uwaga: Ten problem został rozwiązany w programie VS 2017 15.9 3 (wersja zapoznawcza)</span><span class="sxs-lookup"><span data-stu-id="b4858-142">Note: This has been fixed in VS 2017 15.9 Preview 3</span></span>

## <a name="issues-fixed-in-this-release"></a><span data-ttu-id="b4858-143">Problemy rozwiązane w tej wersji</span><span class="sxs-lookup"><span data-stu-id="b4858-143">Issues fixed in this release</span></span>

### <a name="bugs"></a><span data-ttu-id="b4858-144">Usterki</span><span class="sxs-lookup"><span data-stu-id="b4858-144">Bugs</span></span>
#### <a name="signing"></a><span data-ttu-id="b4858-145">podpisywanie</span><span class="sxs-lookup"><span data-stu-id="b4858-145">Signing</span></span>
* <span data-ttu-id="b4858-146">Podpisywanie: Instalowanie podpisany pakiet w trybie offline środowiska [#7008](https://github.com/NuGet/Home/issues/7008) — rozwiązane w 4.8.1</span><span class="sxs-lookup"><span data-stu-id="b4858-146">Signing: Installing signed package in offline environment [#7008](https://github.com/NuGet/Home/issues/7008) -- Fixed in 4.8.1</span></span>
* <span data-ttu-id="b4858-147">Podpisywania:: niepoprawna Sprawdź adres URL — [#7174](https://github.com/NuGet/Home/issues/7174)</span><span class="sxs-lookup"><span data-stu-id="b4858-147">Signing:  incorrect URL check - [#7174](https://github.com/NuGet/Home/issues/7174)</span></span>
* <span data-ttu-id="b4858-148">Podpisywania: gdy pakiet jest repozytorium podpisane - Sprawdź integralność pakietu w RepositorySignatureVerifier [#6926](https://github.com/NuGet/Home/issues/6926)</span><span class="sxs-lookup"><span data-stu-id="b4858-148">Signing:  check package integrity in RepositorySignatureVerifier when package is repository countersigned - [#6926](https://github.com/NuGet/Home/issues/6926)</span></span>
* <span data-ttu-id="b4858-149">"Podczas sprawdzania integralności pakietu nie powiodło się."</span><span class="sxs-lookup"><span data-stu-id="b4858-149">"Package Integrity check failed."</span></span> <span data-ttu-id="b4858-150">powinna mieć identyfikator pakietu w wiadomości (i kod błędu) - [#6944](https://github.com/NuGet/Home/issues/6944)</span><span class="sxs-lookup"><span data-stu-id="b4858-150">should have package ID in message (and error code) - [#6944](https://github.com/NuGet/Home/issues/6944)</span></span>
* <span data-ttu-id="b4858-151">Repozytorium podpisany weryfikacji pakietu zezwala na pakiety podpisane przez innego certyfikatu — [#6884](https://github.com/NuGet/Home/issues/6884)</span><span class="sxs-lookup"><span data-stu-id="b4858-151">Repository signed package verification allows packages signed by different certificate - [#6884](https://github.com/NuGet/Home/issues/6884)</span></span>
* <span data-ttu-id="b4858-152">Adres URL sygnatury czasowej — podpisywania - NuGet nie może być https://?</span><span class="sxs-lookup"><span data-stu-id="b4858-152">NuGet - Signing - Timestamp URL can not be https:// ?</span></span><span data-ttu-id="b4858-153"> - [#6871](https://github.com/NuGet/Home/issues/6871)</span><span class="sxs-lookup"><span data-stu-id="b4858-153"> - [#6871](https://github.com/NuGet/Home/issues/6871)</span></span>
* <span data-ttu-id="b4858-154">Nie NullRef w scenariuszu pakowania NuSpec, również zwiększyć opcji - [#6866](https://github.com/NuGet/Home/issues/6866)</span><span class="sxs-lookup"><span data-stu-id="b4858-154">Don't NullRef in NuSpec packing scenario, also improve options - [#6866](https://github.com/NuGet/Home/issues/6866)</span></span>
* <span data-ttu-id="b4858-155">Pamięć jest nieprawidłowy podczas aktualizowania informacji o osoby podpisującej podczas dodawania sygnatury czasowej do kontrasygnaturze - [#6840](https://github.com/NuGet/Home/issues/6840)</span><span class="sxs-lookup"><span data-stu-id="b4858-155">Memory is invalid while updating signer info when adding timestamp to countersignature - [#6840](https://github.com/NuGet/Home/issues/6840)</span></span>
* <span data-ttu-id="b4858-156">Podpisywanie: usuwanie wyjątków CTL — [#6794](https://github.com/NuGet/Home/issues/6794)</span><span class="sxs-lookup"><span data-stu-id="b4858-156">Signing:  remove CTL exceptions - [#6794](https://github.com/NuGet/Home/issues/6794)</span></span>
* <span data-ttu-id="b4858-157">Podpisywanie: contentUrl musi być typu HTTPS - [#6777](https://github.com/NuGet/Home/issues/6777)</span><span class="sxs-lookup"><span data-stu-id="b4858-157">Signing:  contentUrl MUST be HTTPS - [#6777](https://github.com/NuGet/Home/issues/6777)</span></span>
* <span data-ttu-id="b4858-158">Podpisywanie: SignedPackageVerifierSettings.VSClientDefaultPolicy jest nieużywany - [#6601](https://github.com/NuGet/Home/issues/6601)</span><span class="sxs-lookup"><span data-stu-id="b4858-158">Signing:  SignedPackageVerifierSettings.VSClientDefaultPolicy is unused - [#6601](https://github.com/NuGet/Home/issues/6601)</span></span>


#### <a name="pack"></a><span data-ttu-id="b4858-159">pakiet</span><span class="sxs-lookup"><span data-stu-id="b4858-159">Pack</span></span>
* <span data-ttu-id="b4858-160">Przywracanie i kompilacja powinna być niepotrzebne w przypadku używania dotnet.exe do pakietu nuspec - [#6866](https://github.com/NuGet/Home/issues/6866)</span><span class="sxs-lookup"><span data-stu-id="b4858-160">restore and build should not be needed when using dotnet.exe to pack nuspec - [#6866](https://github.com/NuGet/Home/issues/6866)</span></span>
* <span data-ttu-id="b4858-161">Zezwalaj na pusty zastąpienia tokenów w NuspecProperties - [#6722](https://github.com/NuGet/Home/issues/6722)</span><span class="sxs-lookup"><span data-stu-id="b4858-161">Allow empty replacement tokens in NuspecProperties  - [#6722](https://github.com/NuGet/Home/issues/6722)</span></span>
* <span data-ttu-id="b4858-162">PackTask zgłasza obiektu NullReferenceException, gdy określona jest NuspecProperties - [#4649](https://github.com/NuGet/Home/issues/4649)</span><span class="sxs-lookup"><span data-stu-id="b4858-162">PackTask throws NullReferenceException when NuspecProperties is specified - [#4649](https://github.com/NuGet/Home/issues/4649)</span></span>

#### <a name="accessibility"></a><span data-ttu-id="b4858-163">Ułatwienia dostępu</span><span class="sxs-lookup"><span data-stu-id="b4858-163">Accessibility</span></span>
* <span data-ttu-id="b4858-164">[Ułatwień dostępu.] Ciąg "Wersja wstępna" pod przyciskiem pakiet jest objęta jego opis pakietu w interfejsie użytkownika PM - [#4504](https://github.com/NuGet/Home/issues/4504)</span><span class="sxs-lookup"><span data-stu-id="b4858-164">[Accessibility] String ‘Prerelease’ under package button is covered by its package description in PM UI - [#4504](https://github.com/NuGet/Home/issues/4504)</span></span>
* <span data-ttu-id="b4858-165">[Ułatwień dostępu.] Pakiet źródła listy rozwijanej i przycisk Ustawienia obcięte podczas wybierania "Microsoft Visual Studio w tryb Offline pakietami" w interfejsie użytkownika PM - [#4502](https://github.com/NuGet/Home/issues/4502)</span><span class="sxs-lookup"><span data-stu-id="b4858-165">[Accessibility] Package source drop down and settings button truncated when selecting ‘Microsoft Visual Studio Offline Packages’ in PM UI - [#4502](https://github.com/NuGet/Home/issues/4502)</span></span>

#### <a name="powershell-management-console-pmc"></a><span data-ttu-id="b4858-166">Konsola zarządzania programu PowerShell (PMC)</span><span class="sxs-lookup"><span data-stu-id="b4858-166">Powershell Management Console (PMC)</span></span>
* <span data-ttu-id="b4858-167">`Update-Package` powoduje ignorowanie zakresu wersji PackageReference - [#6775](https://github.com/NuGet/Home/issues/6775)</span><span class="sxs-lookup"><span data-stu-id="b4858-167">`Update-Package` ignores PackageReference version range - [#6775](https://github.com/NuGet/Home/issues/6775)</span></span>
* <span data-ttu-id="b4858-168">`Update-Package -reinstall` rozwiązanie problemu szerokiego — [#3127](https://github.com/NuGet/Home/issues/3127)</span><span class="sxs-lookup"><span data-stu-id="b4858-168">`Update-Package -reinstall` solution wide issue - [#3127](https://github.com/NuGet/Home/issues/3127)</span></span>
* <span data-ttu-id="b4858-169">`Update-Package [packagename] -reinstall` Ponownie instaluje wszystkie pakiety, a nie tylko jedno nazwane - [#737](https://github.com/NuGet/Home/issues/737)</span><span class="sxs-lookup"><span data-stu-id="b4858-169">`Update-Package [packagename] -reinstall` reinstalls all packages instead of just the named one - [#737](https://github.com/NuGet/Home/issues/737)</span></span>
* <span data-ttu-id="b4858-170">Można zaktualizować do pakietu NuGet nieznajdujące się na liście za pomocą konsoli Menedżera pakietów - [#4553](https://github.com/NuGet/Home/issues/4553)</span><span class="sxs-lookup"><span data-stu-id="b4858-170">Can update to unlisted NuGet package from the Package Manager Console - [#4553](https://github.com/NuGet/Home/issues/4553)</span></span>

#### <a name="misc"></a><span data-ttu-id="b4858-171">Różne</span><span class="sxs-lookup"><span data-stu-id="b4858-171">Misc</span></span>
* <span data-ttu-id="b4858-172">Aby naprawić `NuGet update self` NuGet.Commandline nupkg nie powinny być semver2.0 - [#7116](https://github.com/NuGet/Home/issues/7116)</span><span class="sxs-lookup"><span data-stu-id="b4858-172">To fix `NuGet update self` NuGet.Commandline nupkg should not be semver2.0 - [#7116](https://github.com/NuGet/Home/issues/7116)</span></span>
* <span data-ttu-id="b4858-173">Ulepszenie środowiska z błędami instalacji NU1107 - [#7107](https://github.com/NuGet/Home/issues/7107)</span><span class="sxs-lookup"><span data-stu-id="b4858-173">Improve experiences with NU1107 install failures - [#7107](https://github.com/NuGet/Home/issues/7107)</span></span>
* <span data-ttu-id="b4858-174">Serializacja GetAuthenticationCredentialRequest jest niepoprawna — [#6983](https://github.com/NuGet/Home/issues/6983)</span><span class="sxs-lookup"><span data-stu-id="b4858-174">The serialization of GetAuthenticationCredentialRequest is incorrect - [#6983](https://github.com/NuGet/Home/issues/6983)</span></span>
* <span data-ttu-id="b4858-175">NuGet programu Visual Studio AsyncPackage ładuje się po zainicjowaniu wyłączone przez wątek interfejsu użytkownika — [#6976](https://github.com/NuGet/Home/issues/6976)</span><span class="sxs-lookup"><span data-stu-id="b4858-175">NuGet Visual Studio AsyncPackage fails to load when initialized off the UI thread - [#6976](https://github.com/NuGet/Home/issues/6976)</span></span>
* <span data-ttu-id="b4858-176">Przywracanie zgłasza potrzeb mylące błędy z informacją project.json — [#6959](https://github.com/NuGet/Home/issues/6959)</span><span class="sxs-lookup"><span data-stu-id="b4858-176">Restore is reporting misleading errors stating project.json is needed - [#6959](https://github.com/NuGet/Home/issues/6959)</span></span>
* <span data-ttu-id="b4858-177">Interfejs użytkownika Menedżera pakietów: podgląd zmian, przycisk ok, które nie są automatycznie użyteczny, klawiatura — [#6893](https://github.com/NuGet/Home/issues/6893)</span><span class="sxs-lookup"><span data-stu-id="b4858-177">Package manager UI : preview changes, ok button not automatically useable by keyboard - [#6893](https://github.com/NuGet/Home/issues/6893)</span></span>
* <span data-ttu-id="b4858-178">RestoreSources są ignorowane w przypadku projektu z odwołania p2p - [#6776](https://github.com/NuGet/Home/issues/6776)</span><span class="sxs-lookup"><span data-stu-id="b4858-178">RestoreSources are ignored for project with p2p references - [#6776](https://github.com/NuGet/Home/issues/6776)</span></span>
* <span data-ttu-id="b4858-179">Tworzenie projektu testu jednostkowego przy użyciu .NET Framework szablon zostanie otwarty starszego modelu projektu z pliku packages.config - [#6736](https://github.com/NuGet/Home/issues/6736)</span><span class="sxs-lookup"><span data-stu-id="b4858-179">Creating unit test project using .NET Framework template will open older project model with packages.config - [#6736](https://github.com/NuGet/Home/issues/6736)</span></span>
* <span data-ttu-id="b4858-180">Zezwalaj na odwołanie do projektu do zastąpienia zależność pakietu - [#6536](https://github.com/NuGet/Home/issues/6536)</span><span class="sxs-lookup"><span data-stu-id="b4858-180">allow project reference to override package dependency - [#6536](https://github.com/NuGet/Home/issues/6536)</span></span>
* <span data-ttu-id="b4858-181">Udostępnianie NoDefaultExcludes w zadaniu programu MSBuild - [#6450](https://github.com/NuGet/Home/issues/6450)</span><span class="sxs-lookup"><span data-stu-id="b4858-181">Expose NoDefaultExcludes in MSBuild task - [#6450](https://github.com/NuGet/Home/issues/6450)</span></span>
* <span data-ttu-id="b4858-182">Komunikat o stanie dla "Wyczyść wszystkie NuGet Cache(s)" mogą być ukrywane przy zmianie rozmiaru okna - [#5938](https://github.com/NuGet/Home/issues/5938)</span><span class="sxs-lookup"><span data-stu-id="b4858-182">Status message for "Clear All NuGet Cache(s)" can be hidden on window resize - [#5938](https://github.com/NuGet/Home/issues/5938)</span></span>


[<span data-ttu-id="b4858-183">Lista wszystkie problemy rozwiązane w tej wersji</span><span class="sxs-lookup"><span data-stu-id="b4858-183">List of all issues fixed in this release</span></span>](https://github.com/NuGet/Home/issues?q=is%3Aissue+is%3Aclosed+milestone%3A%224.8")