---
title: Klient w wersji 3 NuGet i interfejsów API NuGetGallery
description: NuGet i interfejsów API NuGetGallery są zmieniające się i nie jest jeszcze udokumentowane, ale przykłady są dostępne w blogu Dave Glick.
author: karann-msft
ms.author: karann
manager: unnir
ms.date: 01/09/2018
ms.topic: conceptual
ms.openlocfilehash: b3b912b4af388a578378c15ad9241ed8ec0de75e
ms.sourcegitcommit: 2a6d200012cdb4cbf5ab1264f12fecf9ae12d769
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2018
ms.locfileid: "34817115"
---
# <a name="nuget-client-sdk"></a><span data-ttu-id="43fe3-103">Klienta NuGet zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="43fe3-103">NuGet Client SDK</span></span>

<span data-ttu-id="43fe3-104">Stale ewoluuje NuGet w wersji 3 klienta i interfejsów API NuGetGallery i pracujemy nad o stabilna powierzchni tego będziemy wkrótce dokumentu.</span><span class="sxs-lookup"><span data-stu-id="43fe3-104">The NuGet v3 Client and NuGetGallery APIs are constantly evolving and we are working on having a stable surface area that we can document soon.</span></span>

<span data-ttu-id="43fe3-105">Do tego czasu można znaleźć przykłady i dokumentację dla niektórych interfejsu API w z następującego cyklu blogów przez Dave Glick:</span><span class="sxs-lookup"><span data-stu-id="43fe3-105">In the meantime, you can find examples and documentation for some of the API in the following blog series by Dave Glick:</span></span>

- [<span data-ttu-id="43fe3-106">Eksploracja NuGet w wersji 3 bibliotek, część 1: wprowadzenie i pojęć</span><span class="sxs-lookup"><span data-stu-id="43fe3-106">Exploring the NuGet v3 Libraries, Part 1: Introduction and concepts</span></span>](http://daveaglick.com/posts/exploring-the-nuget-v3-libraries-part-1)
- [<span data-ttu-id="43fe3-107">Eksploracja NuGet w wersji 3 bibliotek, część 2: wyszukiwanie pakietów</span><span class="sxs-lookup"><span data-stu-id="43fe3-107">Exploring the NuGet v3 Libraries, Part 2: Searching for packages</span></span>](http://daveaglick.com/posts/exploring-the-nuget-v3-libraries-part-2)
- [<span data-ttu-id="43fe3-108">Eksploracja NuGet w wersji 3 bibliotek, część 3: Instalowanie pakietów</span><span class="sxs-lookup"><span data-stu-id="43fe3-108">Exploring the NuGet v3 Libraries, Part 3: Installing packages</span></span>](http://daveaglick.com/posts/exploring-the-nuget-v3-libraries-part-3)

> [!Note]
> <span data-ttu-id="43fe3-109">Wpisy na blogu napisanych wkrótce po **3.4.3** wersja programu NuGet wydane pakietów SDK klienta.</span><span class="sxs-lookup"><span data-stu-id="43fe3-109">These blog posts were written shortly after the **3.4.3** version of the NuGet client SDK packages were released.</span></span>
> <span data-ttu-id="43fe3-110">Nowsze wersje pakietów mogą być niezgodne z informacjami w blogach.</span><span class="sxs-lookup"><span data-stu-id="43fe3-110">Newer versions of the packages may be incompatible with the information in the blog posts.</span></span>