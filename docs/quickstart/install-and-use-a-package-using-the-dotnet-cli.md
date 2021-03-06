---
title: Przewodnik wprowadzający, aby za pomocą NuGet pakiety za pośrednictwem interfejsu wiersza polecenia platformy dotnet
description: Samouczek wskazówki dotyczące procesu o instalowaniu i używaniu pakietu NuGet w projekcie platformy .NET Core.
author: karann-msft
ms.author: karann
ms.date: 01/23/2018
ms.topic: quickstart
ms.openlocfilehash: bb24ccbfdd4a6a94cf7116f16b0862871e176e50
ms.sourcegitcommit: 1d1406764c6af5fb7801d462e0c4afc9092fa569
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43549279"
---
# <a name="quickstart-install-and-use-a-package-using-the-dotnet-cli"></a>Szybki Start: Instalowanie i używanie pakietu przy użyciu interfejsu wiersza polecenia platformy dotnet

Pakiety NuGet zawierają kodu wielokrotnego użytku, które inni deweloperzy zapewnić dostępność do użycia w projektach. Zobacz [co to jest NuGet?](../What-is-NuGet.md) w tle. Pakiety zostaną zainstalowane do projektu .NET Core przy użyciu `dotnet add package` polecenia zgodnie z opisem w tym artykule, aby popularnej [Newtonsoft.Json](https://www.nuget.org/packages/Newtonsoft.Json/) pakietu.

Po zakończeniu instalacji można znaleźć pakietu w kodzie za pomocą `using <namespace>` gdzie \<przestrzeni nazw\> jest właściwa dla pakietu jest używany. Następnie można użyć interfejsu API pakietu.

> [!Tip]
> **Rozpoczynać nuget.org**: przeglądania nuget.org znajduje się, jak .NET deweloperzy zazwyczaj znajdują składników ponownego wykorzystania w swoich aplikacjach. Można wyszukać nuget.org bezpośrednio lub znaleźć i zainstalować pakiety w programie Visual Studio, jak pokazano w tym artykule.

## <a name="prerequisites"></a>Wymagania wstępne

- [Zestawu .NET Core SDK](https://www.microsoft.com/net/download/), która zapewnia `dotnet` narzędzie wiersza polecenia.

## <a name="create-a-project"></a>Tworzenie projektu

Można zainstalować pakietów NuGet do projektu .NET pewnego rodzaju. W tym przewodniku Utwórz prosty projekt konsoli .NET Core w następujący sposób:

1. Utwórz folder dla projektu.

1. Utwórz projekt za pomocą następującego polecenia:

    ```cli
    dotnet new console
    ```

1. Użyj `dotnet run` do przetestowania, czy aplikacja została utworzona prawidłowo.

## <a name="add-the-newtonsoftjson-nuget-package"></a>Dodaj pakiet Newtonsoft.Json NuGet

1. Użyj następującego polecenia, aby zainstalować `Newtonsoft.json` pakietu:

    ```cli
    dotnet add package Newtonsoft.Json
    ```

2. Po zakończeniu działania polecenia Otwórz `.csproj` plik, aby zobaczyć odwołania dodane:

    ```xml
   <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.3" />
   </ItemGroup>
    ```

## <a name="use-the-newtonsoftjson-api-in-the-app"></a>Użyj pakietu Newtonsoft.Json interfejsu API w aplikacji

1. Otwórz `Program.cs` pliku i Dodaj następujący wiersz w górnej części pliku:

    ```cs
    using Newtonsoft.Json;
    ```

1. Dodaj następujący kod przed `class Program` wiersza:

    ```cs
    public class Account
    {
        public string Name { get; set; }
        public string Email { get; set; }
        public DateTime DOB { get; set; }
    }
    ```

1. Zastąp `Main` funkcji następującym kodem:

    ```cs
    static void Main(string[] args)
    {
        Account account = new Account
        {
            Name = "John Doe",
            Email = "john@nuget.org",
            DOB = new DateTime(1980, 2, 20, 0, 0, 0, DateTimeKind.Utc),
        };

        string json = JsonConvert.SerializeObject(account, Formatting.Indented);
        Console.WriteLine(json);
    }
    ```

1. Kompilowanie i uruchamianie aplikacji za pomocą `dotnet run` polecenia. Dane wyjściowe powinny być reprezentacji JSON `Account` obiektu w kodzie:

    ```output
    {
      "Name": "John Doe",
      "Email": "john@nuget.org",
      "DOB": "1980-02-20T00:00:00Z"
    }
    ```

## <a name="related-articles"></a>Powiązane artykuły

- [Omówienie i przepływ pracy zużycia pakietu](../consume-packages/overview-and-workflow.md)
- [Znajdowanie i wybieranie pakietów](../consume-packages/finding-and-choosing-packages.md)
- [Sposoby, aby zainstalować pakiet](../consume-packages/ways-to-install-a-package.md)
- [Konfigurowanie zachowania programu NuGet](../consume-packages/configuring-nuget-behavior.md)
