---
title: "Przywracanie NuGet błędy i ostrzeżenia odwołania | Dokumentacja firmy Microsoft"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.date: 12/13/2017
ms.topic: reference
ms.prod: nuget
ms.technology: 
ms.assetid: b76b8a00-7155-4163-b533-894086d2ef78
description: "Pełną dokumentację dla ostrzeżeń i błędów wystawione przez NuGet w czasie przywracania pakietu"
keywords: "NuGet błędy, ostrzeżenia NuGet diagnostyki"
ms.reviewer:
- anangaur
- karann-msft
- unniravindranathan
ms.openlocfilehash: 3423e30eae07ff0c70a010576b8e701be027b847
ms.sourcegitcommit: d0ba99bfe019b779b75731bafdca8a37e35ef0d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2017
---
# <a name="errors-and-warnings"></a>Błędy i ostrzeżenia

W NuGet 4.3.0 błędy i ostrzeżenia są numerowane zgodnie z opisem w tym temacie i zawierają szczegółowe informacje pozwalające rozwiązać problemy związane z. 

Błędy i ostrzeżenia wymienione w tym miejscu są dostępne tylko w przypadku [na podstawie PackageReference](../Consume-Packages/Package-References-in-Project-Files.md) projektów i NuGet 4.3.0. NuGet honoruje także właściwości programu MSBuild tłumienie ostrzeżeń lub podniesienie ich poziomu błędy. Aby uzyskać więcej informacji, zobacz [porady: pomijanie ostrzeżeń kompilatora](https://docs.microsoft.com/visualstudio/ide/how-to-suppress-compiler-warnings) w dokumentacji programu Visual Studio.

**Błędy**

| Grupa | Błąd liczby |
| --- | --- |
| [Nieprawidłowy błędów na wejściu](#invalid-input-errors) | [NU1001](#nu1001), [NU1002](#nu1002), [NU1003](#nu1003) |
| [Brak błędów pakietu i projektu](#missing-package-and-project-errors) | [NU1100](#nu1100), [NU1101](#nu1101), [NU1102](#nu1102), [NU1103](#nu1103), [NU1104](#nu1104), [NU1105](#nu1105), [ NU1106](#nu1106), [NU1107](#nu1107) (wcześniej NU1607) [NU1108](#nu1107) (wcześniej NU1606) |
| [Błędy zgodności](#compatibility-errors) | [NU1201](#nu1201), [NU1202](#nu1202), [NU1203](#nu1203), [NU1401](#nu1401) |

**Ostrzeżenia**

| Grupa | Numery ostrzeżeń |
| --- | --- |
| [Nieprawidłowy wejściowy ostrzeżenia](#invalid-input-warnings) | [NU1501](#nu1501), [NU1502](#nu1502), [NU1503](#nu1503) |
| [Nieoczekiwany pakietu wersji ostrzeżenia](#unexpected-package-version-warnings) | [NU1601](#nu1601), [NU1602](#nu1602), [NU1603](#nu1603), [NU1604](#nu1604), [NU1605](#nu1605) |
| [Mechanizm rozpoznawania konfliktu ostrzeżenia](#resolver-conflict-warnings) | [NU1608](#nu1608) |
| [Ostrzeżenia rezerwowy pakietu](#package-fallback-warnings) | [NU1701](#nu1701) |
| [Źródła danych ostrzeżenia](#feed-warnings) | [NU1801](#nu1801) |
| [NuGet wewnętrzne błędy i ostrzeżenia](#nuget-internal-errors-and-warnings) | [NU1000](#nu1000), [NU1500](#nu1500) |

## <a name="invalid-input-errors"></a>Nieprawidłowy błędów na wejściu

[NU1001](#nu1001) | [NU1002](#nu1002) | [NU1003](#nu1003)

### <a name="nu1001"></a>NU1001

| | |
| --- | --- |
| **Problem** | Projekt nie zawiera co najmniej jeden struktury. |
| **Typowe przyczyny** | Projekt nie zawiera `TargetFramework` lub `TargetFrameworks` właściwości. |
| **Przykładowy komunikat** | *ProjA projektu nie określa żadnych docelowych platform w c:\tmp\projA.csproj* |

### <a name="nu1002"></a>NU1002

| | |
| --- | --- |
| **Problem** | Nieprawidłowa kombinacja danych wejściowych oraz wyczyść — słowo kluczowe. |
| **Typowe przyczyny** | Wyczyść nie mogą być łączone z innymi elementami wejściowymi. |
| **Przykładowy komunikat** | *"CLEAR" nie można używać w połączeniu z innymi wartości* |

### <a name="nu1003"></a>NU1003

| | |
| --- | --- |
| **Problem** | `PackageTargetFallback`i `AssetTargetFallback` Podaj inaczej wybierania zasobów i nie mogą być używane razem. |
| **Typowe przyczyny** | Zarówno `PackageTargetFallback` i `AssetTargetFallback` istnieje w projekcie. |
| **Przykładowy komunikat** | *PackageTargetFallback i AssetTargetFallback nie mogą być używane razem. Usuń odwołania PackageTargetFallback(deprecated) ze środowiska projektu.* |

## <a name="missing-package-and-project-errors"></a>Brak błędów pakietu i projektu

[NU1100](#nu1100) | [NU1101](#nu1101) | [NU1102](#nu1102) | [NU1103](#nu1103) | [NU1104 ](#nu1104)  |  [NU1105](#nu1105) | [NU1106](#nu1106)

### <a name="nu1100"></a>NU1100

| | |
| --- | --- |
| **Problem** | Grupa zależności nie można rozpoznać. Jest to problem rodzajowy dla typów, które nie są pakiety lub projektów. |
| **Typowe przyczyny** | Projekt zawiera zależności elementu, który nie istnieje. |
| **Przykładowy komunikat** | *Nie można rozpoznać System.Missing dla net45* |

### <a name="nu1101"></a>NU1101

| | |
| --- | --- |
| **Problem** | Nie można odnaleźć pakietu na wszystkich źródeł. |
| **Typowe przyczyny** | Brak źródła poprawny pakiet lub identyfikator pakietu jest nieprawidłowa. |
| **Przykładowy komunikat** | *Nie można odnaleźć pakietu System.Missing. Żadne pakiety nie istnieje z tym identyfikatorem w źródłach: dotnet core, dotnet roslyn, nuget.org* |

### <a name="nu1102"></a>NU1102

| | |
| --- | --- |
| **Problem** | Identyfikator pakietu został znaleziony, lecz nie można odnaleźć wersji w zakresie określonym zależności na żadnym z źródeł. |
| **Typowe przyczyny** | Brak źródła poprawny pakiet lub zakres zależności jest niepoprawny. Pakiet, a użytkownik nie może być określony zakres. Użytkownik może być konieczne przełączenie się do wersji dostępnych w przypadku tego pakietu jest odwołuje się projekt bezpośrednio. |
| **Przykładowy komunikat** | *Nie można odnaleźć pakietu NuGet.Versioning z wersją (> = 9.0.1)<br/> — wersje 30 znalezione w usłudze nuget.org [najbliższej wersji: 4.0.0]<br/> — wersje znaleziono 10 w dotnet buildtools [najbliższej wersji: 4.0.0-rc-2129]<br/> -znaleziono 9 wersje w NuGetVolatile [najbliższej wersji: 3.0.0-beta-00032]<br/> -znaleziono wersje 0 w podstawowej platformy dotnet<br/> -znaleziono wersje 0 w dotnet roslyn* |

### <a name="nu1103"></a>NU1103

| | |
| --- | --- |
| **Problem** | Nie odnaleziono żadnych stabilne wersje w zakresie zależności. Wersje wstępne znaleziono, ale nie są dozwolone. |
| **Typowe przyczyny** | Projekt określony stabilną wersję dla zakresu zależności. Użytkownicy muszą zmienić zakres wersji, aby uwzględnić wersje wstępne. |
| **Przykładowy komunikat** | *Nie można odnaleźć pakietu stabilna NuGet.Versioning z wersją (> = 3.0.0)<br/> — wersje znaleziono 10 w dotnet buildtools [najbliższej wersji: 4.0.0-rc-2129]<br/> -znaleziono 9 wersje w NuGetVolatile [najbliższej wersji: 3.0.0-beta-00032] <br/> -Znaleziono wersje 0 w podstawowej platformy dotnet<br/> -znaleziono wersje 0 w dotnet roslyn* |

### <a name="nu1104"></a>NU1104

| | |
| --- | --- |
| **Problem** | Wskazuje element ProjectReference do pliku, który nie istnieje. |
| **Typowe przyczyny** | Brakuje pliku projektu z dysku lub odniesienia jest nieprawidłowa. |
| **Przykładowy komunikat** | *Odwołanie do projektu nie istnieje "c:\a.csproj". Sprawdź, czy odwołanie do projektu jest prawidłowa i czy istnieje plik projektu.* |

### <a name="nu1105"></a>NU1105

| | |
| --- | --- |
| **Problem** | Plik projektu istnieje, ale go nie dostarczono żadnych informacji przywracania. |
| **Typowe przyczyny** | W programie Visual Studio to może oznaczać, że projekt jest zwolniony. W wierszu polecenia to może oznaczać, że plik jest uszkodzony lub nie zawiera niestandardowego po elemencie docelowym importów potrzebne do odzyskiwania do odczytu projektu. |
| **Przykładowy komunikat** | *Nie można odczytać informacji o projekcie dla "c:\a.csproj". Plik projektu może być nieprawidłowe lub brakujące elementy docelowe, wymaganych do przywrócenia.* |

### <a name="nu1106"></a>NU1106

| | |
| --- | --- |
| **Problem** | Nie można rozpoznać zależności ograniczenia. |
| **Typowe przyczyny** | Pakiety zawierają zależność od dokładnej wersji pakietu zamiast nieograniczoną zakresów. |
| **Przykładowy komunikat** | *Nie można zrealizować żądań będących w konflikcie dla {id}: {konflikt path} Framework: {docelowy wykres}* |

< name = "NU1107 ></a>

### <a name="nu1107-previously-nu1607"></a>NU1107 (wcześniej NU1607)

| | |
| --- | --- |
| **Problem** | Nie można rozpoznać ograniczenia zależności między pakietami. |
| **Typowe przyczyny** | Pakiety z ograniczeniami zależności na dokładną wersję nie zezwalają na inne pakiety w razie potrzeby zwiększyć wersji. |
| **Przykładowy komunikat** | *Konflikt wersji dla NuGet.Versioning wykryte. Pakiet odwoływać się bezpośrednio z projektu, aby rozwiązać ten problem.<br/>  NuGet.Versioning (= 3.5.0) -> NuGet.Packaging 3.5.0<br/> NuGet.Configuration 4.0.0 -> NuGet.Versioning (= 4.0.0)* |

< name = "NU1108 ></a>

### <a name="nu1108-previously-nu1606"></a>NU1108 (wcześniej NU1606)

| | |
| --- | --- |
| **Problem** | Wykryto zależność cykliczną. |
| **Typowe przyczyny** | Pakiet jest autoryzowane. |
| **Przykładowy komunikat** | *Wykryto cykl: A -> B -> A* |

## <a name="compatibility-errors"></a>Błędy zgodności

[NU1201](#nu1201) | [NU1202](#nu1202) | [NU1203](#nu1203) | [NU1401](#nu1401)

### <a name="nu1201"></a>NU1201

| | |
| --- | --- |
| **Problem** | Zależności projektu nie zawiera struktury zgodne z bieżącego projektu. |
| **Typowe przyczyny** | Platforma docelowa projektu jest wyższą wersję niż odbierającą projektu. |
| **Przykładowy komunikat** | *ServerWeb projektu nie jest zgodny z netstandard1.3 (. Krótkich nazw NETStandard, Version = w wersji 1.3). Projekt obsługuje ServerWeb:<br/> -netstandard1.6 (. Krótkich nazw NETStandard, Version = w wersji 1.6)<br/> -netcoreapp1.0 (. NETCoreApp, Version = 1.0)* |

### <a name="nu1202"></a>NU1202

| | |
| --- | --- |
| **Problem** | Pakiet zależności nie zawiera żadnych zasobów, które są zgodne z projektem. |
| **Typowe przyczyny** | Pakiet nie obsługuje platformy docelowej projektu. |
| **Przykładowy komunikat** | *Pakiet System.ComponentModel.EventBasedAsync 4.0.11 nie jest zgodny z netstandard1.3 (. Krótkich nazw NETStandard, Version = w wersji 1.3). Pakiet obsługuje System.ComponentModel.EventBasedAsync 4.0.11:<br/> -monoandroid10 (MonoAndroid, wersja = 1.0)<br/> -monotouch10 (MonoTouch, wersja = 1.0)<br/> -net45 (. NETFramework, Version = 4.5)<br/> -netcore50 (. NETCore, Version = v5.0)<br/> -netstandard1.0 (. Krótkich nazw NETStandard, Version = 1.0)<br/> -przenośny net45 + win8 + wp8 + wpa81 (. NETPortable, wersja = v0.0, profil = Profile259)<br/> — Windows 8 (Windows, wersja = w wersji 8.0)<br/> -wp8 (WindowsPhone, wersja = w wersji 8.0)<br/> -wpa81 (WindowsPhoneApp, wersja = v8.1)<br/> — xamarinios10 ( Xamarin.iOS,Version=v1.0)<br/> -xamarinmac20 (Xamarin.Mac,Version=v2.0)<br/> -xamarintvos10 (Xamarin.TVOS,Version=v1.0)<br/> -xamarinwatchos10 (Xamarin.WatchOS,Version=v1.0)*|

### <a name="nu1203"></a>NU1203

| | |
| --- | --- |
| **Problem** | Pakiet nie obsługuje projektu `RuntimeIdentifier`. |
| **Typowe przyczyny** | Pakiet nie obsługuje bieżącej `RuntimeIdentifier`. Zmień `RuntimeIdentifier` wartości używanych w projekcie, jeśli to konieczne. |
| **Przykładowy komunikat** | *System.Example 1.0.0 udostępnia zestaw odwołania czasu kompilowania dla a.dll na net461, ale nie nie zgodny zestaw czasu wykonywania.* |

### <a name="nu1401"></a>NU1401

| | |
| --- | --- |
| **Problem** | Pakiet wymaga funkcji lub struktur nie są obecnie obsługiwane przez zainstalowaną wersję programu NuGet. |
| **Typowe przyczyny** | Uaktualnij program NuGet, aby rozwiązać problem. |
| **Przykładowy komunikat** | *Pakiet "NuGet.Versioning" wymaga wersji klienta "5.0.0" NuGet lub nowszej, ale bieżąca wersja NuGet to "4.3.0". Aby uaktualnić narzędzie NuGet, przejdź do http://docs.nuget.org/consume/installing-nuget.* |

## <a name="invalid-input-warnings"></a>Nieprawidłowy wejściowy ostrzeżenia

[NU1501](#nu1501) | [NU1502](#nu1502) | [NU1503](#nu1503)

### <a name="nu1501"></a>NU1501

| | |
| --- | --- |
| **Problem** | Przywracanie projektu próbuje działać na nie został znaleziony. |
| **Typowe przyczyny** | Brak projektu. |
| **Przykładowy komunikat** | *Folder "c:\projects\a" nie zawiera projektu do przywrócenia.* |

### <a name="nu1502"></a>NU1502

| | |
| --- | --- |
| **Problem** | `RuntimeSupports`zawiera nieprawidłowy profil. |
| **Typowe przyczyny** | Nie znaleziono profilu obsługuje w `runtime.json` plik z bieżącego zależności pakietów. |
| **Przykładowy komunikat** | *Profil zgodności nieznany: aaa* |

### <a name="nu1503"></a>NU1503

| | |
| --- | --- |
| **Problem** | Zależności projektu nie importuje obiekty docelowe przywracania NuGet. Ten jest podobny do NU1105, ale w tym miejscu projektu zostanie pominięty i zignorowany zamiast powoduje wszystkie przywracania się niepowodzeniem. W złożonych rozwiązań są często innych typów projektów, które mogą nie obsługiwać przywracania. |
| **Typowe przyczyny** | Może to nastąpić dla projektów, które nie należy importować wspólne właściwości/cele, które są automatycznie importowane przywracania. Jeśli projekt nie trzeba przywrócić możesz go zignorować. |
| **Przykładowy komunikat** | *Pomijanie przywracania dla projektu "c:\a.csproj". Plik projektu może być nieprawidłowe lub brakujące elementy docelowe, wymaganych do przywrócenia.* |

## <a name="unexpected-package-version-warnings"></a>Nieoczekiwany pakietu wersji ostrzeżenia

[NU1601](#nu1601) | [NU1602](#nu1602) | [NU1603](#nu1603) | [NU1604](#nu1604) | [NU1605](#nu1605)

### <a name="nu1601"></a>NU1601

| | |
| --- | --- |
| **Problem** | Zależności bezpośrednich projektu był upadku na wyższą wersję niż określonego projektu. |
| **Typowe przyczyny** | Inny pakiet zależności wymagane wyższą wersję i upadku pakietu w. |
| **Przykładowy komunikat** | *Określoną zależnością było NuGet.Versioning (> = 3.5.0), ale ostatecznie otrzymano NuGet.Versioning 4.0.0.* |

### <a name="nu1602"></a>NU1602

| | |
| --- | --- |
| **Problem** | Zależność pakietu brak dolnej granicy. To nie zezwala na przywracania znaleźć *najlepszego dopasowania*. Każdy przywracania będzie przestawiany dół próby znalezienia starszej wersji, który może być używany. Oznacza to, że przywracanie przejdzie do trybu online, aby sprawdzić wszystkie źródła zawsze zamiast pakietów, które już istnieją w folderze pakietów użytkowników. |
| **Typowe przyczyny** | Jest to zazwyczaj błąd tworzenia pakietu. |
| **Przykładowy komunikat** | *NuGet.Packaging 4.0.0 nie zapewnia włącznie dolna granica dla zależności NuGet.Versioning (> 3.5.0). Przybliżony najlepsze dopasowanie 3.6.0 został rozwiązany.* |

### <a name="nu1603"></a>NU1603

| | |
| --- | --- |
| **Problem** | Zależność pakietu określonej wersji, którego nie można odnaleźć. Nowsza wersja użyto zamiast tego, który różni się od pakietu opracowania przed.<br/><br/>Oznacza to, że przywracanie nie znalazł *najlepszego dopasowania*. Każdy przywracania będzie przestawiany dół próby znalezienia starszej wersji, który może być używany. Oznacza to, że przywracanie przejdzie do trybu online, aby sprawdzić wszystkie źródła zawsze zamiast pakietów, które już istnieją w folderze pakietów użytkowników. |
| **Typowe przyczyny** | Źródła pakietu nie zawierają wersja oczekiwana dolnej granicy. Jeśli nie zostało zwolnione pakietu oczekiwano może to być błąd tworzenia pakietu. |
| **Przykładowy komunikat** | NuGet.Packaging 4.0.0 zależy od NuGet.Versioning (> = 4.0.0), ale nie można odnaleźć 4.0.0. Przybliżony najlepsze dopasowanie 5.0.0 został rozwiązany. |

### <a name="nu1604"></a>NU1604

| | |
| --- | --- |
| **Problem** | Zależności projektu nie definiuje dolną granicą.<br/><br/>Oznacza to, że przywracanie nie znalazł *najlepszego dopasowania*. Każdy przywracania będzie przestawiany dół próby znalezienia starszej wersji, który może być używany. Oznacza to, że przywracanie przejdzie do trybu online, aby sprawdzić wszystkie źródła zawsze zamiast pakietów, które już istnieją w folderze pakietów użytkowników. |
| **Typowe przyczyny** | Projektu *PackageReference* *wersji* można zaktualizować atrybutu, aby uwzględnić dolną granicą. |
| **Przykładowy komunikat** | *Projekt zależności NuGet.Versioning (< = od 9.0.0) Nowak zawiera włącznie dolnej granicy. Dolna granica należy uwzględnić w wersji zależności, aby zapewnić wyniki przywracania na poziomie.* |

### <a name="nu1605"></a>NU1605

| | |
| --- | --- |
| **Problem** | Pakiet zależności określić ograniczenia wersji za pomocą nowszej wersji pakietu niż przywracania ostatecznie rozwiązane. |
| **Typowe przyczyny** | Najbliższej wins podczas rozpoznawania pakietów. Bliżej położonego pakietu na wykresie mogą mieć zastąpione odległymi pakiet. |
| **Przykładowy komunikat** | *Wykryto starszą wersję pakietu: NuGet.Versioning z 4.0.0 do 3.5.0. Odwoływać się bezpośrednio z projektu, aby wybrać inną wersję pakietu.<br/>  NuGet.Packaging 3.5.0 -> NuGet.Versioning 3.5.0<br/> NuGet.Commands 4.0.0 -> NuGet.Configuration 4.0.0 -> NuGet.Versioning 4.0.0* |

## <a name="resolver-conflict-warnings"></a>Mechanizm rozpoznawania konfliktu ostrzeżenia

[NU1608](#nu1608)

### <a name="nu1608"></a>NU1608

| | |
| --- | --- |
| **Problem** | Usuń pakiet jest większa niż umożliwia ograniczenie zależności. W niektórych przypadkach jest to zamierzone i można pominąć to ostrzeżenie. |
| **Typowe przyczyny** | Pakiet bezpośrednio odwołuje się projekt spowoduje zastąpienie ograniczenia zależności z innymi pakietami.   |
| **Przykładowy komunikat** | *Wersja pakietu wykrytych poza ograniczenia zależności: x 1.0.0 wymaga y (= 1.0.0), ale wersja y 2.0.0 został rozwiązany.* |

## <a name="package-fallback-warnings"></a>Ostrzeżenia rezerwowy pakietu

[NU1701](#nu1701)

### <a name="nu1701"></a>NU1701

| | |
| --- | --- |
| **Problem** | *PackageTargetFallback/AssetTargetFallback* zostało użyte do wybrania zasoby z pakietu. To ostrzeżenie, aby umożliwić użytkownikowi wiedzieć, że zasoby nie mogą być 100% zgodny. |
| **Typowe przyczyny** | Pakiet nie obsługuje platformy projektu. |
| **Przykładowy komunikat** | *Pakiet "NuGet.Versioning" został przywrócony przy użyciu "portable net45 + win8" zamiast platformy docelowej projektu "netstandard1.5". Ten pakiet nie może być całkowicie zgodne z projektem.* |

## <a name="feed-warnings"></a>Źródła danych ostrzeżenia

[NU1801](#nu1801)

### <a name="nu1801"></a>NU1801

| | |
| --- | --- |
| **Problem** | Wystąpił błąd podczas odczytywania źródła po `IgnoreFailedSources` jest ustawiona na wartość true, konwersją niekrytyczny ostrzeżenie. To może zawierać żadnych komunikatów i jest rodzajowy. |
| **Typowe przyczyny** | Źródło jest nieprawidłowe. |
| **Przykładowy komunikat** | n/d |

## <a name="nuget-internal-errors-and-warnings"></a>NuGet wewnętrzne błędy i ostrzeżenia

[NU1000](#nu1000) | [NU1500](#nu1500)

### <a name="nu1000"></a>NU1000

| | |
| --- | --- |
| **Problem** | Nieokreślony błąd wewnętrzny z pakietu NuGet. |
| **Typowe przyczyny** | Sprawdź dzienniki, aby uzyskać więcej informacji |

### <a name="nu1500"></a>NU1500

| | |
| --- | --- |
| **Problem** | Nieokreślony ostrzeżenie wewnętrzny z pakietu NuGet. |
| **Typowe przyczyny** | Sprawdź dzienniki, aby uzyskać więcej informacji |