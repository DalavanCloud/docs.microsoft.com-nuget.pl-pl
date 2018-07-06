---
title: Omówienie programu NuGet interfejsu API
description: Interfejs API NuGet jest zestaw punktów końcowych HTTP, które mogą służyć do pobierania pakietów, pobrać metadanych, publikowanie nowych pakietów itp.
author: joelverhagen
ms.author: jver
manager: skofman
ms.date: 10/26/2017
ms.topic: reference
ms.reviewer: kraigb
ms.openlocfilehash: a638dba005c14bff4b2e668e2d6ca527a67b94a9
ms.sourcegitcommit: 3eab9c4dd41ea7ccd2c28bb5ab16f6fbbec13708
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31820004"
---
# <a name="nuget-api"></a><span data-ttu-id="28b91-103">NuGet interfejsu API</span><span class="sxs-lookup"><span data-stu-id="28b91-103">NuGet API</span></span>

<span data-ttu-id="28b91-104">Interfejs API NuGet jest zestaw punktów końcowych HTTP, które może służyć do pobierania pakietów, pobrać metadanych publikowanie nowych pakietów i wykonywać większości innych operacji dostępne oficjalnego klientów NuGet z.</span><span class="sxs-lookup"><span data-stu-id="28b91-104">The NuGet API is a set of HTTP endpoints that can be used to download packages, fetch metadata, publish new packages, and perform most other operations available in the official NuGet clients.</span></span>

<span data-ttu-id="28b91-105">Ten interfejs API jest używany przez klienta NuGet w Visual Studio, nuget.exe i interfejsu wiersza polecenia platformy .NET w celu wykonania operacji NuGet, takich jak [ `dotnet restore` ](/dotnet/articles/core/preview3/tools/dotnet-restore), wyszukiwanie w interfejsie użytkownika programu Visual Studio i [ `nuget.exe push` ](../tools/cli-ref-push.md).</span><span class="sxs-lookup"><span data-stu-id="28b91-105">This API is used by the NuGet client in Visual Studio, nuget.exe, and the .NET CLI to perform NuGet operations such as [`dotnet restore`](/dotnet/articles/core/preview3/tools/dotnet-restore), search in the Visual Studio UI, and [`nuget.exe push`](../tools/cli-ref-push.md).</span></span>

<span data-ttu-id="28b91-106">Należy pamiętać, w niektórych przypadkach nuget.org ma dodatkowe wymagania, które nie są wymuszane przez inne źródła pakietu.</span><span class="sxs-lookup"><span data-stu-id="28b91-106">Note in some cases, nuget.org has additional requirements that are not enforced by other package sources.</span></span> <span data-ttu-id="28b91-107">Te różnice są udokumentowane przez [protokołów nuget.org](nuget-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="28b91-107">These differences are documented by the [nuget.org Protocols](nuget-protocols.md).</span></span>

## <a name="service-index"></a><span data-ttu-id="28b91-108">Indeks usługi</span><span class="sxs-lookup"><span data-stu-id="28b91-108">Service index</span></span>

<span data-ttu-id="28b91-109">Punkt wejścia dla interfejsu API jest dokumentem JSON w znanej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="28b91-109">The entry point for the API is a JSON document in a well known location.</span></span> <span data-ttu-id="28b91-110">Ten dokument jest nazywany **indeksu usługi**.</span><span class="sxs-lookup"><span data-stu-id="28b91-110">This document is called the **service index**.</span></span> <span data-ttu-id="28b91-111">Lokalizacja indeks usługi nuget.org jest `https://api.nuget.org/v3/index.json`.</span><span class="sxs-lookup"><span data-stu-id="28b91-111">The location of the service index for nuget.org is `https://api.nuget.org/v3/index.json`.</span></span>

<span data-ttu-id="28b91-112">Ten dokument JSON zawiera listę *zasobów* co mieć inne funkcje i spełnienia innych przypadków użycia.</span><span class="sxs-lookup"><span data-stu-id="28b91-112">This JSON document contains a list of *resources* which provide different functionality and fulfill different use cases.</span></span>

<span data-ttu-id="28b91-113">Klienci, którzy obsługują interfejs API powinna obsługiwać co najmniej jednego z tych adresów URL indeksu usługi jako sposób nawiązywania połączenia źródła odpowiednich pakietów.</span><span class="sxs-lookup"><span data-stu-id="28b91-113">Clients that support the API should accept one or more of these service index URL as the means of connecting to the respective package sources.</span></span>

<span data-ttu-id="28b91-114">Aby uzyskać więcej informacji o indeksie usługi, zobacz [jego dokumentacja interfejsu API](service-index.md).</span><span class="sxs-lookup"><span data-stu-id="28b91-114">For more information about the service index, see [its API reference](service-index.md).</span></span>

## <a name="versioning"></a><span data-ttu-id="28b91-115">Przechowywanie wersji</span><span class="sxs-lookup"><span data-stu-id="28b91-115">Versioning</span></span>

<span data-ttu-id="28b91-116">Interfejs API jest w wersji 3 NuGet protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="28b91-116">The API is version 3 of NuGet's HTTP protocol.</span></span> <span data-ttu-id="28b91-117">Ten protokół jest czasami nazywany "API w wersji 3."</span><span class="sxs-lookup"><span data-stu-id="28b91-117">This protocol is sometimes referred to as "the V3 API."</span></span> <span data-ttu-id="28b91-118">Te dokumenty odwołanie będzie odwoływać się do tej wersji protokołu po prostu jako "interfejsu API."</span><span class="sxs-lookup"><span data-stu-id="28b91-118">These reference documents will refer to this version of the protocol simply as "the API."</span></span>

<span data-ttu-id="28b91-119">Wersja schematu indeksu usługi jest określane przez `version` właściwości w indeksie usługi.</span><span class="sxs-lookup"><span data-stu-id="28b91-119">The service index schema version is indicated by the `version` property in the service index.</span></span> <span data-ttu-id="28b91-120">Interfejs API wymaga, że ciąg wersji ma numer wersji głównej `3`.</span><span class="sxs-lookup"><span data-stu-id="28b91-120">The API mandates that the version string has a major version number of `3`.</span></span> <span data-ttu-id="28b91-121">Nierozdzielające zmiany do schematu indeksu usługi, zostanie zwiększona wersja pomocnicza ciąg wersji.</span><span class="sxs-lookup"><span data-stu-id="28b91-121">As non-breaking changes are made to the service index schema, the version string's minor version will be increased.</span></span>

<span data-ttu-id="28b91-122">Starszych klientów (takich jak nuget.exe 2.x) nie obsługują interfejsu API w wersji 3 i obsługują tylko starsze V2 interfejsu API, który nie jest opisane w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="28b91-122">Older clients (such as nuget.exe 2.x) do not support the V3 API and only support the older V2 API, which is not documented here.</span></span>

<span data-ttu-id="28b91-123">Interfejsu API w wersji 3 NuGet nosi nazwę jako takie ponieważ jest on następnika interfejsu API w wersji 2, który został zaimplementowany przez wersję 2.x oficjalnego klienta NuGet protokół OData na podstawie.</span><span class="sxs-lookup"><span data-stu-id="28b91-123">The NuGet V3 API is named as such because it's the successor of the V2 API, which was the OData-based protocol implemented by the 2.x version of the official NuGet client.</span></span> <span data-ttu-id="28b91-124">Interfejsu API w wersji 3 najpierw jest obsługiwana przez wersję 3.0 oficjalnego klienta NuGet i nadal jest najnowsza wersja główna protocol w wersji obsługiwany przez klienta NuGet, 4.0 i.</span><span class="sxs-lookup"><span data-stu-id="28b91-124">The V3 API was first supported by the 3.0 version of the official NuGet client and is still the latest major protocol version supported by the NuGet client, 4.0 and on.</span></span> 

<span data-ttu-id="28b91-125">Wprowadzono zmiany protokołu bez podziału do interfejsu API od czasu pierwszej wersji.</span><span class="sxs-lookup"><span data-stu-id="28b91-125">Non-breaking protocol changes have been made to the API since it was first release.</span></span>

## <a name="resources-and-schema"></a><span data-ttu-id="28b91-126">Zasoby i schematu</span><span class="sxs-lookup"><span data-stu-id="28b91-126">Resources and schema</span></span>

<span data-ttu-id="28b91-127">**Indeksu usługi** opisano różne zasoby.</span><span class="sxs-lookup"><span data-stu-id="28b91-127">The **service index** describes a variety of resources.</span></span> <span data-ttu-id="28b91-128">Bieżący zestaw zasobów obsługiwane są następujące:</span><span class="sxs-lookup"><span data-stu-id="28b91-128">The current set of supported resources are as follows:</span></span>

<span data-ttu-id="28b91-129">Nazwa zasobu</span><span class="sxs-lookup"><span data-stu-id="28b91-129">Resource name</span></span>                                                          | <span data-ttu-id="28b91-130">Wymagane</span><span class="sxs-lookup"><span data-stu-id="28b91-130">Required</span></span> | <span data-ttu-id="28b91-131">Opis</span><span class="sxs-lookup"><span data-stu-id="28b91-131">Description</span></span>
---------------------------------------------------------------------- | -------- | -----------
[`PackagePublish`](package-publish-resource.md)                        | <span data-ttu-id="28b91-132">Tak</span><span class="sxs-lookup"><span data-stu-id="28b91-132">yes</span></span>      | <span data-ttu-id="28b91-133">Wypychanie i usunąć lub unlist pakietów.</span><span class="sxs-lookup"><span data-stu-id="28b91-133">Push and delete (or unlist) packages.</span></span>
[`SearchQueryService`](search-query-service-resource.md)               | <span data-ttu-id="28b91-134">Tak</span><span class="sxs-lookup"><span data-stu-id="28b91-134">yes</span></span>      | <span data-ttu-id="28b91-135">Filtr i wyszukaj pakietów według słów kluczowych.</span><span class="sxs-lookup"><span data-stu-id="28b91-135">Filter and search for packages by keyword.</span></span>
[`RegistrationsBaseUrl`](registration-base-url-resource.md)            | <span data-ttu-id="28b91-136">Tak</span><span class="sxs-lookup"><span data-stu-id="28b91-136">yes</span></span>      | <span data-ttu-id="28b91-137">Pobierz pakiet metadanych.</span><span class="sxs-lookup"><span data-stu-id="28b91-137">Get package metadata.</span></span>
[`PackageBaseAddress`](package-base-address-resource.md)               | <span data-ttu-id="28b91-138">Tak</span><span class="sxs-lookup"><span data-stu-id="28b91-138">yes</span></span>      | <span data-ttu-id="28b91-139">Pobierz zawartość pakietu (.nupkg).</span><span class="sxs-lookup"><span data-stu-id="28b91-139">Get package content (.nupkg).</span></span>
[`SearchAutocompleteService`](search-autocomplete-service-resource.md) | <span data-ttu-id="28b91-140">Brak</span><span class="sxs-lookup"><span data-stu-id="28b91-140">no</span></span>       | <span data-ttu-id="28b91-141">Odnajdź identyfikatorów pakietów i wersje przez podciąg.</span><span class="sxs-lookup"><span data-stu-id="28b91-141">Discover package IDs and versions by substring.</span></span>
[`ReportAbuseUriTemplate`](report-abuse-resource.md)                   | <span data-ttu-id="28b91-142">Brak</span><span class="sxs-lookup"><span data-stu-id="28b91-142">no</span></span>       | <span data-ttu-id="28b91-143">Utworzyć adres URL "zgłaszania nadużyć" strona sieci web.</span><span class="sxs-lookup"><span data-stu-id="28b91-143">Construct a URL to access a "report abuse" web page.</span></span>
[`Catalog`](catalog-resource.md)                                       | <span data-ttu-id="28b91-144">Brak</span><span class="sxs-lookup"><span data-stu-id="28b91-144">no</span></span>       | <span data-ttu-id="28b91-145">Pełną dokumentację wszystkie zdarzenia pakietu.</span><span class="sxs-lookup"><span data-stu-id="28b91-145">Full record of all package events.</span></span>

<span data-ttu-id="28b91-146">Ogólnie rzecz biorąc wszystkie dane nieznakowe zwrócony przez zasób interfejsu API są serializowane, za pomocą formatu JSON.</span><span class="sxs-lookup"><span data-stu-id="28b91-146">In general, all non-binary data returned by a API resource are serialized using JSON.</span></span> <span data-ttu-id="28b91-147">Odpowiedź Schemat zwrócony przez każdy zasób w indeksie usługi zdefiniowano indywidualnie dla tego zasobu.</span><span class="sxs-lookup"><span data-stu-id="28b91-147">The response schema returned by each resource in the service index is defined individually for that resource.</span></span> <span data-ttu-id="28b91-148">Aby uzyskać więcej informacji na temat każdego z zasobów zobacz tematy wymienione powyżej.</span><span class="sxs-lookup"><span data-stu-id="28b91-148">For more information about each resource, see the topics listed above.</span></span>

> [!Note]
> <span data-ttu-id="28b91-149">Jeśli źródło nie implementuje `SearchAutocompleteService` wszystkie zachowania autouzupełniania, które powinny być wyłączone bezpiecznie.</span><span class="sxs-lookup"><span data-stu-id="28b91-149">When a source does not implement `SearchAutocompleteService` any autocomplete behavior should be disabled gracefully.</span></span> <span data-ttu-id="28b91-150">Gdy `ReportAbuseUriTemplate` nie jest zaimplementowana, oficjalnego powróci klienta NuGet do nuget.org raport nadużycia adresu URL (śledzonych przez [NuGet domowych #4924](https://github.com/NuGet/Home/issues/4924)).</span><span class="sxs-lookup"><span data-stu-id="28b91-150">When `ReportAbuseUriTemplate` is not implemented, the official NuGet client falls back to nuget.org's report abuse URL (tracked by [NuGet/Home#4924](https://github.com/NuGet/Home/issues/4924)).</span></span> <span data-ttu-id="28b91-151">Inni klienci mogą zdecydować się na po prostu nie przedstawiają adres URL raportu nadużyć dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="28b91-151">Other clients may opt to simply not show a report abuse URL to the user.</span></span>

## <a name="timestamps"></a><span data-ttu-id="28b91-152">Znaczniki czasu</span><span class="sxs-lookup"><span data-stu-id="28b91-152">Timestamps</span></span>

<span data-ttu-id="28b91-153">Wszystkie sygnatury czasowe zwracane przez interfejs API są UTC lub w przeciwnym razie są określane za pomocą [ISO 8601](https://www.iso.org/iso-8601-date-and-time-format.html) reprezentacji.</span><span class="sxs-lookup"><span data-stu-id="28b91-153">All timestamps returned by the API are UTC or are otherwise specified using [ISO 8601](https://www.iso.org/iso-8601-date-and-time-format.html) representation.</span></span> 

## <a name="http-methods"></a><span data-ttu-id="28b91-154">Metody HTTP</span><span class="sxs-lookup"><span data-stu-id="28b91-154">HTTP methods</span></span>

<span data-ttu-id="28b91-155">Zlecenie</span><span class="sxs-lookup"><span data-stu-id="28b91-155">Verb</span></span>   | <span data-ttu-id="28b91-156">Zastosowanie</span><span class="sxs-lookup"><span data-stu-id="28b91-156">Use</span></span>
------ | -----------
<span data-ttu-id="28b91-157">POBIERZ</span><span class="sxs-lookup"><span data-stu-id="28b91-157">GET</span></span>    | <span data-ttu-id="28b91-158">Wykonuje operację tylko do odczytu, zazwyczaj podczas pobierania danych.</span><span class="sxs-lookup"><span data-stu-id="28b91-158">Performs a read-only operation, typically retrieving data.</span></span>
<span data-ttu-id="28b91-159">HEAD</span><span class="sxs-lookup"><span data-stu-id="28b91-159">HEAD</span></span>   | <span data-ttu-id="28b91-160">Pobiera nagłówki odpowiedzi dla odpowiedniego `GET` żądania.</span><span class="sxs-lookup"><span data-stu-id="28b91-160">Fetches the response headers for the corresponding `GET` request.</span></span>
<span data-ttu-id="28b91-161">UMIEŚĆ</span><span class="sxs-lookup"><span data-stu-id="28b91-161">PUT</span></span>    | <span data-ttu-id="28b91-162">Tworzy z zasobem, który nie istnieje lub, jeśli istnieje, aktualizuje.</span><span class="sxs-lookup"><span data-stu-id="28b91-162">Creates a resource that doesn't exist or, if it does exist, updates it.</span></span> <span data-ttu-id="28b91-163">Niektóre zasoby mogą nie obsługiwać aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="28b91-163">Some resources may not support update.</span></span>
<span data-ttu-id="28b91-164">DELETE</span><span class="sxs-lookup"><span data-stu-id="28b91-164">DELETE</span></span> | <span data-ttu-id="28b91-165">Usuwa lub unlists zasobu.</span><span class="sxs-lookup"><span data-stu-id="28b91-165">Deletes or unlists a resource.</span></span>

## <a name="http-status-codes"></a><span data-ttu-id="28b91-166">Kody stanu HTTP</span><span class="sxs-lookup"><span data-stu-id="28b91-166">HTTP status codes</span></span>

<span data-ttu-id="28b91-167">Kod</span><span class="sxs-lookup"><span data-stu-id="28b91-167">Code</span></span> | <span data-ttu-id="28b91-168">Opis</span><span class="sxs-lookup"><span data-stu-id="28b91-168">Description</span></span>
---- | -----
<span data-ttu-id="28b91-169">200</span><span class="sxs-lookup"><span data-stu-id="28b91-169">200</span></span>  | <span data-ttu-id="28b91-170">Sukces, a treść odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="28b91-170">Success, and there is a response body.</span></span>
<span data-ttu-id="28b91-171">201</span><span class="sxs-lookup"><span data-stu-id="28b91-171">201</span></span>  | <span data-ttu-id="28b91-172">Utworzono sukcesu i zasobu.</span><span class="sxs-lookup"><span data-stu-id="28b91-172">Success, and the resource was created.</span></span>
<span data-ttu-id="28b91-173">202</span><span class="sxs-lookup"><span data-stu-id="28b91-173">202</span></span>  | <span data-ttu-id="28b91-174">Sukces, żądanie zostało zaakceptowane, ale niektóre pracy może być niekompletna i zakończonych asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="28b91-174">Success, the request has been accepted but some work may still be incomplete and completed asynchronously.</span></span>
<span data-ttu-id="28b91-175">204</span><span class="sxs-lookup"><span data-stu-id="28b91-175">204</span></span>  | <span data-ttu-id="28b91-176">Sukces, ale brak treści odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="28b91-176">Success, but there is no response body.</span></span>
<span data-ttu-id="28b91-177">301</span><span class="sxs-lookup"><span data-stu-id="28b91-177">301</span></span>  | <span data-ttu-id="28b91-178">Stałe przekierowanie.</span><span class="sxs-lookup"><span data-stu-id="28b91-178">A permanent redirect.</span></span>
<span data-ttu-id="28b91-179">302</span><span class="sxs-lookup"><span data-stu-id="28b91-179">302</span></span>  | <span data-ttu-id="28b91-180">Przekierowanie tymczasowe.</span><span class="sxs-lookup"><span data-stu-id="28b91-180">A temporary redirect.</span></span>
<span data-ttu-id="28b91-181">400</span><span class="sxs-lookup"><span data-stu-id="28b91-181">400</span></span>  | <span data-ttu-id="28b91-182">Parametry w adresie URL lub w treści żądania są nieprawidłowe.</span><span class="sxs-lookup"><span data-stu-id="28b91-182">The parameters in the URL or in the request body aren't valid.</span></span>
<span data-ttu-id="28b91-183">401</span><span class="sxs-lookup"><span data-stu-id="28b91-183">401</span></span>  | <span data-ttu-id="28b91-184">Podane poświadczenia są nieprawidłowe.</span><span class="sxs-lookup"><span data-stu-id="28b91-184">The provided credentials are invalid.</span></span>
<span data-ttu-id="28b91-185">403</span><span class="sxs-lookup"><span data-stu-id="28b91-185">403</span></span>  | <span data-ttu-id="28b91-186">Akcja nie jest dozwolona w podanej podanych poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="28b91-186">The action is not allowed given the provided credentials.</span></span>
<span data-ttu-id="28b91-187">404</span><span class="sxs-lookup"><span data-stu-id="28b91-187">404</span></span>  | <span data-ttu-id="28b91-188">Żądany zasób nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="28b91-188">The requested resource doesn't exist.</span></span>
<span data-ttu-id="28b91-189">409</span><span class="sxs-lookup"><span data-stu-id="28b91-189">409</span></span>  | <span data-ttu-id="28b91-190">Konflikty żądania z istniejącego zasobu.</span><span class="sxs-lookup"><span data-stu-id="28b91-190">The request conflicts with an existing resource.</span></span>
<span data-ttu-id="28b91-191">500</span><span class="sxs-lookup"><span data-stu-id="28b91-191">500</span></span>  | <span data-ttu-id="28b91-192">Usługa napotkała nieoczekiwany błąd.</span><span class="sxs-lookup"><span data-stu-id="28b91-192">The service has encountered an unexpected error.</span></span>
<span data-ttu-id="28b91-193">503</span><span class="sxs-lookup"><span data-stu-id="28b91-193">503</span></span>  | <span data-ttu-id="28b91-194">Usługa jest tymczasowo niedostępna.</span><span class="sxs-lookup"><span data-stu-id="28b91-194">The service is temporarily unavailable.</span></span>

<span data-ttu-id="28b91-195">Wszelkie `GET` żądania skierowane do punktu końcowego interfejsu API może zwrócić przekierowania HTTP (301 lub 302).</span><span class="sxs-lookup"><span data-stu-id="28b91-195">Any `GET` request made to a API endpoint may return an HTTP redirect (301 or 302).</span></span> <span data-ttu-id="28b91-196">Klienci powinna obsługiwać takie przekierowuje obserwując `Location` nagłówka oraz wydawanie kolejnej `GET`.</span><span class="sxs-lookup"><span data-stu-id="28b91-196">Clients should gracefully handle such redirects by observing the `Location` header and issueing a subsequent `GET`.</span></span> <span data-ttu-id="28b91-197">Dokumentację dotyczącą określonych punktów końcowych nie zostanie jawnie wywoływać się, których można użyć przekierowania.</span><span class="sxs-lookup"><span data-stu-id="28b91-197">Documentation concerning specific endpoints will not explicitly call out where redirects may be used.</span></span>

<span data-ttu-id="28b91-198">W przypadku kodu stanu 500 poziomu klienta można zaimplementować mechanizm ponawiania uzasadnione.</span><span class="sxs-lookup"><span data-stu-id="28b91-198">In the case of a 500-level status code, the client can implement a reasonable retry mechanism.</span></span> <span data-ttu-id="28b91-199">Oficjalna NuGet klienta ponowne próby trzy razy, gdy wystąpią kod stanu 500 poziomu ani błędu TCP/serwera DNS.</span><span class="sxs-lookup"><span data-stu-id="28b91-199">The official NuGet client retries three times when encountering any 500-level status code or TCP/DNS error.</span></span>

## <a name="http-request-headers"></a><span data-ttu-id="28b91-200">Nagłówki żądania HTTP</span><span class="sxs-lookup"><span data-stu-id="28b91-200">HTTP request headers</span></span>

<span data-ttu-id="28b91-201">Nazwa</span><span class="sxs-lookup"><span data-stu-id="28b91-201">Name</span></span>                     | <span data-ttu-id="28b91-202">Opis</span><span class="sxs-lookup"><span data-stu-id="28b91-202">Description</span></span>
------------------------ | -----------
<span data-ttu-id="28b91-203">X-NuGet-ApiKey</span><span class="sxs-lookup"><span data-stu-id="28b91-203">X-NuGet-ApiKey</span></span>           | <span data-ttu-id="28b91-204">Wymagane do wypychania i usuwania, zobacz [ `PackagePublish` zasobów](package-publish-resource.md)</span><span class="sxs-lookup"><span data-stu-id="28b91-204">Required for push and delete, see [`PackagePublish` resource](package-publish-resource.md)</span></span>
<span data-ttu-id="28b91-205">X-NuGet-Client-Version</span><span class="sxs-lookup"><span data-stu-id="28b91-205">X-NuGet-Client-Version</span></span>   | <span data-ttu-id="28b91-206">**Przestarzałe** i zastąpione przez `X-NuGet-Protocol-Version`</span><span class="sxs-lookup"><span data-stu-id="28b91-206">**Deprecated** and replaced by `X-NuGet-Protocol-Version`</span></span>
<span data-ttu-id="28b91-207">X-NuGet-Protocol-Version</span><span class="sxs-lookup"><span data-stu-id="28b91-207">X-NuGet-Protocol-Version</span></span> | <span data-ttu-id="28b91-208">W niektórych przypadkach tylko na nuget.org wymagane, zobacz [protokołów nuget.org](NuGet-Protocols.md)</span><span class="sxs-lookup"><span data-stu-id="28b91-208">Required in certain cases only on nuget.org, see [nuget.org protocols](NuGet-Protocols.md)</span></span>
<span data-ttu-id="28b91-209">X-NuGet-Session-Id</span><span class="sxs-lookup"><span data-stu-id="28b91-209">X-NuGet-Session-Id</span></span>       | <span data-ttu-id="28b91-210">*Opcjonalne*.</span><span class="sxs-lookup"><span data-stu-id="28b91-210">*Optional*.</span></span> <span data-ttu-id="28b91-211">NuGet klientów v4.7 + zidentyfikować żądania HTTP, które są częścią tej samej sesji klienta NuGet.</span><span class="sxs-lookup"><span data-stu-id="28b91-211">NuGet clients v4.7+ identify HTTP requests that are part of the same NuGet client session.</span></span> <span data-ttu-id="28b91-212">Aby uzyskać `PackageReference` operacji przywracania nie jest identyfikatorem jednej sesji w innych sytuacjach, takich jak automatyczne uzupełnianie, i `packages.config` przywracania może istnieć kilka różnych identyfikatora sesji przez ze względu na sposób kod jest brana pod uwagę.</span><span class="sxs-lookup"><span data-stu-id="28b91-212">For `PackageReference` restore operations there is a single session id, for other scenarios such as auto complete, and `packages.config` restore there may be several different session id's due to how the code is factored.</span></span>

## <a name="authentication"></a><span data-ttu-id="28b91-213">Uwierzytelnianie</span><span class="sxs-lookup"><span data-stu-id="28b91-213">Authentication</span></span>

<span data-ttu-id="28b91-214">Do wykonania źródła pakietu do definiowania pozostanie uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="28b91-214">Authentication is left up to the package source implementation to define.</span></span> <span data-ttu-id="28b91-215">Dla nuget.org tylko `PackagePublish` zasób wymaga uwierzytelnienia za pomocą specjalnych nagłówków klucza interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="28b91-215">For nuget.org, only the `PackagePublish` resource requires authentication via a special API key header.</span></span> <span data-ttu-id="28b91-216">Zobacz [ `PackagePublish` zasobów](package-publish-resource.md) szczegółowe informacje.</span><span class="sxs-lookup"><span data-stu-id="28b91-216">See [`PackagePublish` resource](package-publish-resource.md) for details.</span></span>