---
title: Informacje o wersji 2,5 NuGet
description: Informacje o wersji 2.5 NuGet tym znanych problemów, poprawki, dodatkowe funkcje i dcr.
author: karann-msft
ms.author: karann
manager: unnir
ms.date: 11/11/2016
ms.topic: conceptual
ms.openlocfilehash: accea5033e44927259537b5047a4a821babc6146
ms.sourcegitcommit: a6ca160b1e7e5c58b135af4eba0e9463127a59e8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
ms.locfileid: "32045006"
---
# <a name="nuget-25-release-notes"></a><span data-ttu-id="85364-103">Informacje o wersji 2,5 NuGet</span><span class="sxs-lookup"><span data-stu-id="85364-103">NuGet 2.5 Release Notes</span></span>

<span data-ttu-id="85364-104">[Informacje o wersji NuGet 2.2.1](../release-notes/nuget-2.2.1.md) | [NuGet 2.6 informacje o wersji](../release-notes/nuget-2.6.md)</span><span class="sxs-lookup"><span data-stu-id="85364-104">[NuGet 2.2.1 Release Notes](../release-notes/nuget-2.2.1.md) | [NuGet 2.6 Release Notes](../release-notes/nuget-2.6.md)</span></span>

<span data-ttu-id="85364-105">NuGet 2.5 został wydany 25 kwietnia 2013.</span><span class="sxs-lookup"><span data-stu-id="85364-105">NuGet 2.5 was released on April 25, 2013.</span></span> <span data-ttu-id="85364-106">Ta wersja została tak duży, możemy mieli świadomość zmuszony do pomijania w wersji 2.3 i 2.4!</span><span class="sxs-lookup"><span data-stu-id="85364-106">This release was so big, we felt compelled to skip versions 2.3 and 2.4!</span></span> <span data-ttu-id="85364-107">Data, to największy zlecenia, które zostały było programu NuGet, z za pośrednictwem [elementy robocze 160](https://nuget.codeplex.com/workitem/list/advanced?release=NuGet%202.5&status=all) w wersji.</span><span class="sxs-lookup"><span data-stu-id="85364-107">To date, this is the largest release we've had for NuGet, with over [160 work items](https://nuget.codeplex.com/workitem/list/advanced?release=NuGet%202.5&status=all) in the release.</span></span>

## <a name="acknowledgements"></a><span data-ttu-id="85364-108">Potwierdzeń</span><span class="sxs-lookup"><span data-stu-id="85364-108">Acknowledgements</span></span>

<span data-ttu-id="85364-109">Chcielibyśmy Dziękujemy następujące współautorzy zewnętrznych dla ich znaczących wkładów do NuGet 2.5:</span><span class="sxs-lookup"><span data-stu-id="85364-109">We would like to thank the following external contributors for their significant contributions to NuGet 2.5:</span></span>

1. <span data-ttu-id="85364-110">[Danielowi Plaisted](https://www.codeplex.com/site/users/view/dsplaisted) ([@dsplaisted](https://twitter.com/dsplaisted))</span><span class="sxs-lookup"><span data-stu-id="85364-110">[Daniel Plaisted](https://www.codeplex.com/site/users/view/dsplaisted) ([@dsplaisted](https://twitter.com/dsplaisted))</span></span>
    - <span data-ttu-id="85364-111">[#2847](https://nuget.codeplex.com/workitem/2847) — Dodaj MonoAndroid, MonoTouch i MonoMac do listy znanych docelowej framework identyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="85364-111">[#2847](https://nuget.codeplex.com/workitem/2847) - Add MonoAndroid, MonoTouch, and MonoMac to the list of known target framework identifiers.</span></span>
2. <span data-ttu-id="85364-112">[Andres G. Aragoneses](https://www.codeplex.com/site/users/view/knocte) ([@knocte](https://twitter.com/knocte))</span><span class="sxs-lookup"><span data-stu-id="85364-112">[Andres G. Aragoneses](https://www.codeplex.com/site/users/view/knocte) ([@knocte](https://twitter.com/knocte))</span></span>
    - <span data-ttu-id="85364-113">[#2865](https://nuget.codeplex.com/workitem/2865) -Popraw pisownię wyrazu `NuGet.targets` dla z uwzględnieniem wielkości liter systemu operacyjnego</span><span class="sxs-lookup"><span data-stu-id="85364-113">[#2865](https://nuget.codeplex.com/workitem/2865) - Fix spelling of `NuGet.targets` for a case-sensitive OS</span></span>
3. <span data-ttu-id="85364-114">[Dominik Fowler](https://www.codeplex.com/site/users/view/dfowler) ([@davidfowl](https://twitter.com/davidfowl))</span><span class="sxs-lookup"><span data-stu-id="85364-114">[David Fowler](https://www.codeplex.com/site/users/view/dfowler) ([@davidfowl](https://twitter.com/davidfowl))</span></span>
    - <span data-ttu-id="85364-115">Należy kompilacji w jedno rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="85364-115">Make the solution build on Mono.</span></span>
4. <span data-ttu-id="85364-116">[Andrew Theken](https://www.codeplex.com/site/users/view/atheken) ([@atheken](https://twitter.com/atheken))</span><span class="sxs-lookup"><span data-stu-id="85364-116">[Andrew Theken](https://www.codeplex.com/site/users/view/atheken) ([@atheken](https://twitter.com/atheken))</span></span>
    - <span data-ttu-id="85364-117">Napraw na Mono testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="85364-117">Fix unit tests failing on Mono.</span></span>
5. <span data-ttu-id="85364-118">[Olivier Dagenais](https://www.codeplex.com/site/users/view/OliIsCool) ([@OliIsCool](https://twitter.com/oliiscool))</span><span class="sxs-lookup"><span data-stu-id="85364-118">[Olivier Dagenais](https://www.codeplex.com/site/users/view/OliIsCool) ([@OliIsCool](https://twitter.com/oliiscool))</span></span>
    - <span data-ttu-id="85364-119">[#2920](https://nuget.codeplex.com/workitem/2920) — polecenie Pakiet nuget.exe nie propaguje właściwości dla programu MSBuild</span><span class="sxs-lookup"><span data-stu-id="85364-119">[#2920](https://nuget.codeplex.com/workitem/2920) - nuget.exe pack command does not propagate Properties to MSBuild</span></span>
6. <span data-ttu-id="85364-120">[Miroslav Bajtos](https://www.codeplex.com/site/users/view/MiroslavBajtos) ([@bajtos](https://twitter.com/bajtos))</span><span class="sxs-lookup"><span data-stu-id="85364-120">[Miroslav Bajtos](https://www.codeplex.com/site/users/view/MiroslavBajtos) ([@bajtos](https://twitter.com/bajtos))</span></span>
    - <span data-ttu-id="85364-121">[#1511](https://nuget.codeplex.com/workitem/1511) — zmodyfikować XML kod obsługi Aby zachować formatowanie.</span><span class="sxs-lookup"><span data-stu-id="85364-121">[#1511](https://nuget.codeplex.com/workitem/1511) - Modified XML handling code to preserve formatting.</span></span>
7. <span data-ttu-id="85364-122">[ADAM Ralph](http://www.codeplex.com/site/users/view/adamralph) ([@adamralph](https://twitter.com/adamralph))</span><span class="sxs-lookup"><span data-stu-id="85364-122">[Adam Ralph](http://www.codeplex.com/site/users/view/adamralph) ([@adamralph](https://twitter.com/adamralph))</span></span>
    - <span data-ttu-id="85364-123">Rozpoznany wyrazy zostały dodane do słownika niestandardowego, aby umożliwić build.cmd powiodło się.</span><span class="sxs-lookup"><span data-stu-id="85364-123">Added recognized words to custom dictionary to allow build.cmd to succeed.</span></span>
8. [<span data-ttu-id="85364-124">Bruno Roggeri</span><span class="sxs-lookup"><span data-stu-id="85364-124">Bruno Roggeri</span></span>](https://www.codeplex.com/site/users/view/broggeri)
    - <span data-ttu-id="85364-125">Napraw testów jednostkowych w zlokalizowanej wersji programu VS.</span><span class="sxs-lookup"><span data-stu-id="85364-125">Fix unit tests when running in localized VS.</span></span>
9. [<span data-ttu-id="85364-126">Gareth Evans</span><span class="sxs-lookup"><span data-stu-id="85364-126">Gareth Evans</span></span>](https://www.codeplex.com/site/users/view/garethevans)
    - <span data-ttu-id="85364-127">Interfejs wyodrębnione z PackageService</span><span class="sxs-lookup"><span data-stu-id="85364-127">Extracted interface from PackageService</span></span>
10. <span data-ttu-id="85364-128">[Maxime Brugidou](https://www.codeplex.com/site/users/view/brugidou) ([@brugidou](https://twitter.com/brugidou))</span><span class="sxs-lookup"><span data-stu-id="85364-128">[Maxime Brugidou](https://www.codeplex.com/site/users/view/brugidou) ([@brugidou](https://twitter.com/brugidou))</span></span>
     - <span data-ttu-id="85364-129">[#936](https://nuget.codeplex.com/workitem/936) -obsługi zależności projektu podczas pakowania</span><span class="sxs-lookup"><span data-stu-id="85364-129">[#936](https://nuget.codeplex.com/workitem/936) - Handle project dependencies when packing</span></span>
11. <span data-ttu-id="85364-130">[Xavier Decoster](https://www.codeplex.com/site/users/view/XavierDecoster) ([@XavierDecoster](https://twitter.com/xavierdecoster))</span><span class="sxs-lookup"><span data-stu-id="85364-130">[Xavier Decoster](https://www.codeplex.com/site/users/view/XavierDecoster) ([@XavierDecoster](https://twitter.com/xavierdecoster))</span></span>
     - <span data-ttu-id="85364-131">[#2991](https://nuget.codeplex.com/workitem/2991), [#3164](https://nuget.codeplex.com/workitem/3164) — Obsługa Wyczyść hasła tekstu podczas zapisywania poświadczeń dostępu do źródła pakietu w plikach nuget.cofig</span><span class="sxs-lookup"><span data-stu-id="85364-131">[#2991](https://nuget.codeplex.com/workitem/2991), [#3164](https://nuget.codeplex.com/workitem/3164) - Support Clear Text Password when storing package source credentials in nuget.cofig files</span></span>
12. <span data-ttu-id="85364-132">[Kuba Manning](http://www.codeplex.com/site/users/view/jmanning) ([@manningj](https://twitter.com/manningj))</span><span class="sxs-lookup"><span data-stu-id="85364-132">[James Manning](http://www.codeplex.com/site/users/view/jmanning) ([@manningj](https://twitter.com/manningj))</span></span>
     - <span data-ttu-id="85364-133">[#3190](http://nuget.codeplex.com/workitem/3190), [#3191](http://nuget.codeplex.com/workitem/3191) -Get-Package Usuń opis pomocy</span><span class="sxs-lookup"><span data-stu-id="85364-133">[#3190](http://nuget.codeplex.com/workitem/3190), [#3191](http://nuget.codeplex.com/workitem/3191) - Fix Get-Package help description</span></span>

<span data-ttu-id="85364-134">Dziękujemy następującym osobom również do znajdowania usterki z NuGet 2.5 Beta lub RC zatwierdzone i rozwiązać przed ostateczną wersją:</span><span class="sxs-lookup"><span data-stu-id="85364-134">We also appreciate the following individuals for finding bugs with NuGet 2.5 Beta/RC that were approved and fixed before the final release:</span></span>

1. <span data-ttu-id="85364-135">[Tony Wall](https://www.codeplex.com/site/users/view/CodeChief) ([@CodeChief](https://twitter.com/codechief))</span><span class="sxs-lookup"><span data-stu-id="85364-135">[Tony Wall](https://www.codeplex.com/site/users/view/CodeChief) ([@CodeChief](https://twitter.com/codechief))</span></span>
    - <span data-ttu-id="85364-136">[#3200](https://nuget.codeplex.com/workitem/3200) — MSTest przerwanie najnowsza NuGet 2.4 i tworzy 2,5</span><span class="sxs-lookup"><span data-stu-id="85364-136">[#3200](https://nuget.codeplex.com/workitem/3200) - MSTest broken with lastest NuGet 2.4 and 2.5 builds</span></span>

## <a name="notable-features-in-the-release"></a><span data-ttu-id="85364-137">Ważne funkcje w wersji</span><span class="sxs-lookup"><span data-stu-id="85364-137">Notable features in the release</span></span>

### <a name="allow-users-to-overwrite-content-files-that-already-exist"></a><span data-ttu-id="85364-138">Zezwalaj użytkownikom na zastąpienie plików zawartości, które już istnieją</span><span class="sxs-lookup"><span data-stu-id="85364-138">Allow users to overwrite content files that already exist</span></span>

<span data-ttu-id="85364-139">Jedną z najbardziej pożądanych funkcji cały czas została możliwość zastąpienia plików zawartości, które już istnieją na dysku, gdy uwzględnione w pakiecie NuGet.</span><span class="sxs-lookup"><span data-stu-id="85364-139">One of the most requested features of all time has been the ability to overwrite content files that already exist on disk when included in a NuGet package.</span></span> <span data-ttu-id="85364-140">Począwszy od NuGet 2.5 te konflikty zostaną rozpoznane i zostanie wyświetlony monit o zastąpienie plików, należy wcześniej zawsze pliki te zostały pominięte.</span><span class="sxs-lookup"><span data-stu-id="85364-140">Starting with NuGet 2.5, these conflicts are identified and you are prompted to overwrite the files, whereas previously these files were always skipped.</span></span>

![Zastąp pliki zawartości](./media/NuGet-2.5/overwrite-file.png)

<span data-ttu-id="85364-142">"nuget.exe aktualizacji" i "Install-Package" teraz mają nową opcję "-FileConflictAction" można ustawić pewne domyślne dla scenariuszy wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="85364-142">'nuget.exe update' and 'Install-Package' now both have a new option '-FileConflictAction' to set some default for command-line scenarios.</span></span>

<span data-ttu-id="85364-143">Domyślna akcja należy ustawić, gdy plik z pakietu już istnieje w projekcie docelowym.</span><span class="sxs-lookup"><span data-stu-id="85364-143">Set a default action when a file from a package already exists in the target project.</span></span> <span data-ttu-id="85364-144">Wartość "Zastąp" zawsze zastąpienie plików.</span><span class="sxs-lookup"><span data-stu-id="85364-144">Set to 'Overwrite' to always overwrite files.</span></span> <span data-ttu-id="85364-145">Wartość "Ignore" Pomiń pliki.</span><span class="sxs-lookup"><span data-stu-id="85364-145">Set to 'Ignore' to skip files.</span></span> <span data-ttu-id="85364-146">Jeśli nie zostanie określony, pojawi się monit o poszczególnych plików powodujących konflikt.</span><span class="sxs-lookup"><span data-stu-id="85364-146">If not specified, it will prompt for each conflicting file.</span></span>

### <a name="automatic-import-of-msbuild-targets-and-props-files"></a><span data-ttu-id="85364-147">Automatyczne importowanie MSBuild cele i pliki właściwości</span><span class="sxs-lookup"><span data-stu-id="85364-147">Automatic import of MSBuild targets and props files</span></span>

<span data-ttu-id="85364-148">Nowy folder konwencjonalnej został utworzony na najwyższym poziomie pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="85364-148">A new conventional folder has been created at the top level of the NuGet package.</span></span>  <span data-ttu-id="85364-149">Jako elementu równorzędnego do `\lib`, `\content`, i `\tools`, obecnie można uwzględnić `\build` folderu do pakietu.</span><span class="sxs-lookup"><span data-stu-id="85364-149">As a peer to `\lib`, `\content`, and `\tools`, you can now include a `\build` folder in your package.</span></span>  <span data-ttu-id="85364-150">W tym folderze, możesz umieścić dwoma plikami o stałej nazwie `{packageid}.targets` lub `{packageid}.props`.</span><span class="sxs-lookup"><span data-stu-id="85364-150">Under this folder, you can place two files with fixed names, `{packageid}.targets` or `{packageid}.props`.</span></span> <span data-ttu-id="85364-151">Te dwa pliki mogą być bezpośrednio w obszarze `build` lub w obszarze określonej struktury folderów, podobnie jak w innych folderach.</span><span class="sxs-lookup"><span data-stu-id="85364-151">These two files can be either directly under `build` or under framework-specific folders just like the other folders.</span></span> <span data-ttu-id="85364-152">Reguła dla folderu framework najlepiej dopasowane do pobrania jest dokładnie takie same jak te.</span><span class="sxs-lookup"><span data-stu-id="85364-152">The rule for picking the best-matched framework folder is exactly the same as in those.</span></span>

<span data-ttu-id="85364-153">Podczas instalowania NuGet pakietu z plikami \build doda MSBuild `<Import>` elementu w pliku projektu wskazujący `.targets` i `.props` plików.</span><span class="sxs-lookup"><span data-stu-id="85364-153">When NuGet installs a package with \build files, it will add an MSBuild `<Import>` element in the project file pointing to the `.targets` and `.props` files.</span></span> <span data-ttu-id="85364-154">`.props` Plik zostanie dodany u góry, podczas gdy `.targets` plik zostanie dodany do dołu.</span><span class="sxs-lookup"><span data-stu-id="85364-154">The `.props` file is added at the top, whereas the `.targets` file is added to the bottom.</span></span>

### <a name="specify-different-references-per-platform-using-references-element"></a><span data-ttu-id="85364-155">Określ różne odwołania na platformie za pomocą `<References/>` — element</span><span class="sxs-lookup"><span data-stu-id="85364-155">Specify different references per platform using `<References/>` element</span></span>

<span data-ttu-id="85364-156">Przed 2.5 w `.nuspec` pliku użytkownika można określić tylko pliki odwołania, ma zostać dodana dla wszystkich framework.</span><span class="sxs-lookup"><span data-stu-id="85364-156">Before 2.5, in `.nuspec` file, user can only specify the reference files, to be added for all framework.</span></span> <span data-ttu-id="85364-157">Teraz dzięki tej nowej funkcji 2.5 użytkownika można tworzyć `<reference/>` elementu dla każdej z obsługiwanych platform, na przykład:</span><span class="sxs-lookup"><span data-stu-id="85364-157">Now with this new feature in 2.5, user can author the `<reference/>` element for each of the supported platform, for example:</span></span>

```xml
<references>
    <group targetFramework="net45">
        <reference file="a.dll" />
    </group>
    <group targetFramework="netcore45">
        <reference file="b.dll" />
    </group>
    <group>
        <reference file="c.dll" />
    </group>
</references>
```

<span data-ttu-id="85364-158">Poniżej przedstawiono przepływ dla jak NuGet dodaje odwołań do projektów opartych na `.nuspec` pliku:</span><span class="sxs-lookup"><span data-stu-id="85364-158">Here is the flow for how NuGet adds references to projects based on the `.nuspec` file:</span></span>

1. <span data-ttu-id="85364-159">Znajdź `lib` folderu, który jest odpowiedni dla platformy docelowej i Pobierz listę zestawów z tego folderu</span><span class="sxs-lookup"><span data-stu-id="85364-159">Find the `lib` folder that is appropriate for the target framework and get the list of assemblies from that folder</span></span>
1. <span data-ttu-id="85364-160">Oddzielnie znaleźć odwołuje się do grupy, który jest odpowiedni dla platformy docelowej i listę zestawów z tej grupy.</span><span class="sxs-lookup"><span data-stu-id="85364-160">Separately find the references group that is appropriate for the target framework and get the list of assemblies from that group.</span></span> <span data-ttu-id="85364-161">Grupy odwołania bez określonej platformy docelowej jest grupa rezerwowego.</span><span class="sxs-lookup"><span data-stu-id="85364-161">Reference group without target framework specified is the fallback group.</span></span>
1. <span data-ttu-id="85364-162">Znajdź część wspólną dwóch list i używać go jako odwołania do dodania</span><span class="sxs-lookup"><span data-stu-id="85364-162">Find the intersection of the two lists, and use that as the references to add</span></span>

<span data-ttu-id="85364-163">Ta nowa funkcja umożliwia autorów pakiet do użycia funkcji odwołań do zastosowania podzbiór zestawów do różnych platform, gdy byłby normalnie potrzebny do przenoszenia zestawy zduplikowany w wielu `lib` folderów.</span><span class="sxs-lookup"><span data-stu-id="85364-163">This new feature will allow package authors to use the References feature to apply subsets of assemblies to different frameworks when they would otherwise need to carry duplicate assemblies in multiple `lib` folders.</span></span>

<span data-ttu-id="85364-164">Uwaga: należy obecnie używasz pakietu nuget.exe Aby użyć tej funkcji; Eksplorator pakietu NuGet nie obsługuje jeszcze go.</span><span class="sxs-lookup"><span data-stu-id="85364-164">Note: you must presently use nuget.exe pack to use this feature; NuGet Package Explorer does not yet support it.</span></span>

### <a name="update-all-button-to-allow-updating-all-packages-at-once"></a><span data-ttu-id="85364-165">Zaktualizuj wszystkie przycisk umożliwia jednocześnie aktualizowania wszystkich pakietów</span><span class="sxs-lookup"><span data-stu-id="85364-165">Update All button to allow updating all packages at once</span></span>

<span data-ttu-id="85364-166">Wiele osób wiedzieć o polecenia cmdlet programu PowerShell "Pakiet aktualizacji" można zaktualizować wszystkich pakietów; teraz jest prosty sposób, w tym także interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="85364-166">Many of you know about the "Update-Package" PowerShell cmdlet to update all of your packages; now there's an easy way to do this through the UI as well.</span></span>

<span data-ttu-id="85364-167">Aby wypróbować tę funkcję:</span><span class="sxs-lookup"><span data-stu-id="85364-167">To try this feature out:</span></span>

1. <span data-ttu-id="85364-168">Tworzenie nowej aplikacji ASP.NET MVC</span><span class="sxs-lookup"><span data-stu-id="85364-168">Create a new ASP.NET MVC application</span></span>
1. <span data-ttu-id="85364-169">Uruchom okno dialogowe "Manage NuGet Packages"</span><span class="sxs-lookup"><span data-stu-id="85364-169">Launch the 'Manage NuGet Packages' dialog</span></span>
1. <span data-ttu-id="85364-170">Wybierz opcję "Aktualizacji"</span><span class="sxs-lookup"><span data-stu-id="85364-170">Select 'Updates'</span></span>
1. <span data-ttu-id="85364-171">Kliknij przycisk "Aktualizuj wszystkie"</span><span class="sxs-lookup"><span data-stu-id="85364-171">Click the 'Update All' button</span></span>

![Zaktualizuj wszystkie przycisk w oknie dialogowym](./media/NuGet-2.5/update-all.png)

### <a name="improved-project-reference-support-for-nugetexe-pack"></a><span data-ttu-id="85364-173">Odwołanie projektu ulepszone obsługę nuget.exe pakietu</span><span class="sxs-lookup"><span data-stu-id="85364-173">Improved project reference support for nuget.exe Pack</span></span>

<span data-ttu-id="85364-174">Teraz nuget.exe pakiet polecenia procesów przywoływane projekty z następującymi regułami:</span><span class="sxs-lookup"><span data-stu-id="85364-174">Now nuget.exe pack command processes referenced projects with the following rules:</span></span>

1. <span data-ttu-id="85364-175">Jeśli ma przywoływanego projektu odpowiadającego `.nuspec` pliku, np. istnieje plik o nazwie `proj1.nuspec` w tym samym folderze co `proj1.csproj`, następnie ten projekt zostanie dodany jako zależność do pakietu przy użyciu identyfikatora i odczytać wersji z `.nuspec` pliku.</span><span class="sxs-lookup"><span data-stu-id="85364-175">If the referenced project has corresponding `.nuspec` file, e.g. there is a file called `proj1.nuspec` in the same folder as `proj1.csproj`, then this project is added as a dependency to the package, using the id and version read from the `.nuspec` file.</span></span>
1. <span data-ttu-id="85364-176">W przeciwnym razie pliki przywoływanego projektu są połączone w pakiecie.</span><span class="sxs-lookup"><span data-stu-id="85364-176">Otherwise, the files of the referenced project are bundled into the package.</span></span> <span data-ttu-id="85364-177">Następnie projektów odwołuje się ten projekt zostanie przetworzona za pomocą sames rekursywnie reguły.</span><span class="sxs-lookup"><span data-stu-id="85364-177">Then projects referenced by this project will be processed using the sames rules recursively.</span></span>
1. <span data-ttu-id="85364-178">Wszystkie biblioteki DLL, `.pdb`, i `.exe` pliki zostaną dodane.</span><span class="sxs-lookup"><span data-stu-id="85364-178">All DLL, `.pdb`, and `.exe` files are added.</span></span>
1. <span data-ttu-id="85364-179">Wszystkie pliki zawartości są dodawane.</span><span class="sxs-lookup"><span data-stu-id="85364-179">All other content files are added.</span></span>
1. <span data-ttu-id="85364-180">Wszystkie zależności są łączone.</span><span class="sxs-lookup"><span data-stu-id="85364-180">All dependencies are merged.</span></span>

<span data-ttu-id="85364-181">Dzięki temu przywoływanego projektu powinien być traktowany jako zależność, jeśli istnieje `.nuspec` pliku, w przeciwnym razie staje się częścią pakietu.</span><span class="sxs-lookup"><span data-stu-id="85364-181">This allows a referenced project to be treated as a dependency if there is a `.nuspec` file, otherwise, it becomes part of the package.</span></span>

<span data-ttu-id="85364-182">Więcej informacji w tym miejscu: [http://nuget.codeplex.com/workitem/936](http://nuget.codeplex.com/workitem/936)</span><span class="sxs-lookup"><span data-stu-id="85364-182">More details here: [http://nuget.codeplex.com/workitem/936](http://nuget.codeplex.com/workitem/936)</span></span>

### <a name="add-a-minimum-nuget-version-property-to-packages"></a><span data-ttu-id="85364-183">Dodaj właściwość "Minimalna wersja narzędzia NuGet" do pakietów</span><span class="sxs-lookup"><span data-stu-id="85364-183">Add a 'Minimum NuGet Version' property to packages</span></span>

<span data-ttu-id="85364-184">Nowy atrybut metadanych o nazwie "minClientVersion" można teraz wskazać minimalnej wersji klienta NuGet musieli korzystać z pakietem.</span><span class="sxs-lookup"><span data-stu-id="85364-184">A new metadata attribute called 'minClientVersion' can now indicate the minimum NuGet client version required to consume a package.</span></span>

<span data-ttu-id="85364-185">Funkcja ta ułatwia autora pakietu, aby określić, że pakiet będą działać dopiero po określonej wersji programu NuGet.</span><span class="sxs-lookup"><span data-stu-id="85364-185">This feature helps package author to specify that a package will work only after a particular version of NuGet.</span></span> <span data-ttu-id="85364-186">Jak nowe `.nuspec` funkcje zostaną dodane po NuGet 2.5 pakiety będą mogli oświadczeń minimalna wersja narzędzia NuGet.</span><span class="sxs-lookup"><span data-stu-id="85364-186">As new `.nuspec` features are added after NuGet 2.5, packages will be able to claim a minimum NuGet version.</span></span>

```xml
<metadata minClientVersion="2.6">
```

<span data-ttu-id="85364-187">Jeśli użytkownik ma zainstalowane 2.5 NuGet, pakiet zostanie zidentyfikowana jako wymagające 2.6 wizualnych otrzyma użytkownikowi wskazujący, że pakiet nie będzie możliwe do zainstalowania.</span><span class="sxs-lookup"><span data-stu-id="85364-187">If the user has NuGet 2.5 installed and a package is identified as requiring 2.6, visual cues will be given to the user indicating the package will not be installable.</span></span> <span data-ttu-id="85364-188">Użytkownik zostanie następnie z przewodnikiem, aby zaktualizować ich wersja programu NuGet.</span><span class="sxs-lookup"><span data-stu-id="85364-188">The user will then be guided to update their version of NuGet.</span></span>

<span data-ttu-id="85364-189">Poprawia to na istniejące środowisko, gdzie rozpocząć pakietów do zainstalowania, a następnie się nie powieść wskazujący, że wersja schematu nierozpoznany została zidentyfikowana.</span><span class="sxs-lookup"><span data-stu-id="85364-189">This will improve upon the existing experience where packages begin to install but then fail indicating an unrecognized schema version was identified.</span></span>

### <a name="dependencies-are-no-longer-unnecessarily-updated-during-package-installation"></a><span data-ttu-id="85364-190">Zależności już niepotrzebnie są aktualizowane podczas instalacji pakietu aktualizacji</span><span class="sxs-lookup"><span data-stu-id="85364-190">Dependencies are no longer unnecessarily updated during package installation</span></span>

<span data-ttu-id="85364-191">Przed 2.5 NuGet gdy pakiet został zainstalowany, która była uzależniona od pakietu już zainstalowany w projekcie, zależności byłby aktualizowany w ramach nowej instalacji nawet wtedy, gdy istniejąca wersja spełnione zależności.</span><span class="sxs-lookup"><span data-stu-id="85364-191">Before NuGet 2.5, when a package was installed that depended on a package already installed in the project, the dependency would be updated as part of the new installation, even if the existing version satisfied the dependency.</span></span>

<span data-ttu-id="85364-192">Począwszy NuGet 2.5, jeśli wersja zależności już jest spełniony, zależność nie zostanie zaktualizowany podczas inne instalacje pakietu.</span><span class="sxs-lookup"><span data-stu-id="85364-192">Starting with NuGet 2.5, if a dependency version is already satisfied, the dependency will not be updated during other package installations.</span></span>

<span data-ttu-id="85364-193">**Scenariusz:**</span><span class="sxs-lookup"><span data-stu-id="85364-193">**The scenario:**</span></span>

1. <span data-ttu-id="85364-194">Repozytorium źródłowe zawiera pakiet B w wersji 1.0.0 i w wersji 1.0.2.</span><span class="sxs-lookup"><span data-stu-id="85364-194">The source repository contains package B with version 1.0.0 and 1.0.2.</span></span> <span data-ttu-id="85364-195">Zawiera także pakietu A zależy B (> = 1.0.0).</span><span class="sxs-lookup"><span data-stu-id="85364-195">It also contains package A which has a dependency on B (>= 1.0.0).</span></span>
1. <span data-ttu-id="85364-196">Załóżmy, że bieżący projekt ma już wersję pakietu B 1.0.0 zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="85364-196">Assume that the current project already has package B version 1.0.0 installed.</span></span> <span data-ttu-id="85364-197">Teraz ma zostać zainstalowany pakiet A.</span><span class="sxs-lookup"><span data-stu-id="85364-197">Now you want to install package A.</span></span>

<span data-ttu-id="85364-198">**W NuGet 2,2 i starszych:**</span><span class="sxs-lookup"><span data-stu-id="85364-198">**In NuGet 2.2 and older:**</span></span>

* <span data-ttu-id="85364-199">Podczas instalowania pakietu, A, NuGet automatycznie zaktualizuje B 1.0.2, nawet jeśli istniejąca wersja 1.0.0 spełnia już ograniczenie wersji zależności, która jest > = 1.0.0.</span><span class="sxs-lookup"><span data-stu-id="85364-199">When installing package A, NuGet will auto-update B to 1.0.2, even though the existing version 1.0.0 already satisfies the dependency version constraint, which is >= 1.0.0.</span></span>

<span data-ttu-id="85364-200">**W NuGet 2.5 lub nowszej:**</span><span class="sxs-lookup"><span data-stu-id="85364-200">**In NuGet 2.5 and newer:**</span></span>

* <span data-ttu-id="85364-201">NuGet już zaktualizuje B, ponieważ wykrywa, że istniejąca wersja 1.0.0 spełnia ograniczenia wersji zależności.</span><span class="sxs-lookup"><span data-stu-id="85364-201">NuGet will no longer update B, because it detects that the existing version 1.0.0 satisfies the dependency version constraint.</span></span>

<span data-ttu-id="85364-202">W tle więcej na temat tej zmiany, przeczytaj szczegółowe [elementu roboczego](http://nuget.codeplex.com/workitem/1681) oraz powiązanych [wątek dyskusji](http://nuget.codeplex.com/discussions/436712).</span><span class="sxs-lookup"><span data-stu-id="85364-202">For more background on this change, read the detailed [work item](http://nuget.codeplex.com/workitem/1681) as well as the related [discussion thread](http://nuget.codeplex.com/discussions/436712).</span></span>

### <a name="nugetexe-outputs-http-requests-with-detailed-verbosity"></a><span data-ttu-id="85364-203">nuget.exe danych wyjściowych żądań http o poziomie szczegółowości szczegółowe</span><span class="sxs-lookup"><span data-stu-id="85364-203">nuget.exe outputs http requests with detailed verbosity</span></span>

<span data-ttu-id="85364-204">Jeśli występuje problem nuget.exe lub po prostu zastanawiasz się, jakie żądania HTTP są wprowadzane podczas operacji, '-szczegółowości szczegółowe "przełącznika teraz dane wyjściowe obejmują wszystkie żądania HTTP.</span><span class="sxs-lookup"><span data-stu-id="85364-204">If you are troubleshooting nuget.exe or just curious what HTTP requests are made during operations, the '-verbosity detailed' switch will now output all HTTP requests made.</span></span>

![Dane wyjściowe nuget.exe HTTP](./media/NuGet-2.5/verbosity.png)

### <a name="nugetexe-push-now-supports-unc-and-folder-sources"></a><span data-ttu-id="85364-206">wypychania nuget.exe obsługuje teraz źródeł UNC i folderów</span><span class="sxs-lookup"><span data-stu-id="85364-206">nuget.exe push now supports UNC and folder sources</span></span>

<span data-ttu-id="85364-207">Przed NuGet 2.5 podczas próby uruchomienia "nuget.exe push" do źródła pakietu na podstawie ścieżki UNC lub folderu lokalnego powiadomienia wypychanego nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="85364-207">Before NuGet 2.5, if you attempted to run 'nuget.exe push' to a package source based on a UNC path or local folder, the push would fail.</span></span> <span data-ttu-id="85364-208">Z funkcją ostatnio dodane konfiguracji hierarchiczna stało się często nuget.exe trzeba objęcie źródła UNC lub folder lub galerii NuGet oparte na protokole HTTP.</span><span class="sxs-lookup"><span data-stu-id="85364-208">With the recently added hierarchical configuration feature, it had become common for nuget.exe to need to target either a UNC/folder source, or an HTTP-based NuGet Gallery.</span></span>

<span data-ttu-id="85364-209">Zaczynając NuGet 2.5, jeśli nuget.exe identyfikuje źródła UNC lub folder, zostanie przeprowadzone kopiowania plików do źródła.</span><span class="sxs-lookup"><span data-stu-id="85364-209">Starting with NuGet 2.5, if nuget.exe identifies a UNC/folder source, it will perform the file copy to the source.</span></span>

<span data-ttu-id="85364-210">Teraz działa następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="85364-210">The following command will now work:</span></span>

```
nuget push -source \\mycompany\repo\ mypackage.1.0.0.nupkg
```

### <a name="nugetexe-supports-explicitly-specified-config-files"></a><span data-ttu-id="85364-211">nuget.exe obsługuje jawnie określić pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="85364-211">nuget.exe supports explicitly-specified Config files</span></span>

<span data-ttu-id="85364-212">polecenia nuget.exe, które uzyskują dostęp do konfiguracji (wszystkie z wyjątkiem "spec" oraz "pakiet"), teraz obsługują nowy "-ConfigFile" opcja, która wymusza konfiguracji określonego pliku do użycia zamiast domyślnego pliku konfiguracji % AppData%\nuget\Nuget.Config.</span><span class="sxs-lookup"><span data-stu-id="85364-212">nuget.exe commands that access configuration (all except 'spec' and 'pack') now support a new '-ConfigFile' option, which forces a specific config file to be used in place of the default config file at %AppData%\nuget\Nuget.Config.</span></span>

<span data-ttu-id="85364-213">Przykład:</span><span class="sxs-lookup"><span data-stu-id="85364-213">Example:</span></span>

```
nuget sources add -name test -source http://test -ConfigFile C:\test\.nuget\Nuget.Config
```

### <a name="support-for-native-projects"></a><span data-ttu-id="85364-214">Pomoc techniczna dla projektów natywnych</span><span class="sxs-lookup"><span data-stu-id="85364-214">Support for Native projects</span></span>

<span data-ttu-id="85364-215">Z NuGet 2.5 narzędzia NuGet jest teraz dostępna dla projektów natywnych w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="85364-215">With NuGet 2.5, the NuGet tooling is now available for Native projects in Visual Studio.</span></span> <span data-ttu-id="85364-216">Oczekujemy najbardziej natywnego pakietów korzystanie z funkcji importów MSBuild powyżej, przy użyciu narzędzia utworzone przez [projektu CoApp](http://coapp.org).</span><span class="sxs-lookup"><span data-stu-id="85364-216">We expect most native packages will utilize the MSBuild imports feature above, using a tool created by the [CoApp project](http://coapp.org).</span></span> <span data-ttu-id="85364-217">Aby uzyskać więcej informacji, przeczytaj [szczegółowe informacje o narzędziu](http://coapp.org/news/2013-03-27-The-Long-Awaited-post.html) na coapp.org witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="85364-217">For more information, read [the details about the tool](http://coapp.org/news/2013-03-27-The-Long-Awaited-post.html) on the coapp.org website.</span></span>

<span data-ttu-id="85364-218">Nazwa docelowej framework "native" wprowadzono pakietów podczas dołączania plików \build, \content i \tools po zainstalowaniu pakietu do natywnego projektu.</span><span class="sxs-lookup"><span data-stu-id="85364-218">The target framework name of "native" is introduced for packages to include files in \build, \content, and \tools when the package is installed into a native project.</span></span>  <span data-ttu-id="85364-219">\`Lib "folder nie jest używany dla projektów natywnych.</span><span class="sxs-lookup"><span data-stu-id="85364-219">The \`lib` folder is not used for native projects.</span></span>