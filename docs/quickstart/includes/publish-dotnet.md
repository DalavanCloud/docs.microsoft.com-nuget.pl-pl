1. <span data-ttu-id="8076e-101">Zmień folder zawierający `.nupkg` pliku.</span><span class="sxs-lookup"><span data-stu-id="8076e-101">Change to the folder containing the `.nupkg` file.</span></span>

1. <span data-ttu-id="8076e-102">Uruchom następujące polecenie, określając nazwę pakietu i zastępując wartość klucza swój klucz interfejsu API:</span><span class="sxs-lookup"><span data-stu-id="8076e-102">Run the following command, specifying your package name and replacing the key value with your API key:</span></span>

    ```cli
    dotnet nuget push AppLogger.1.0.0.nupkg -k qz2jga8pl3dvn2akksyquwcs9ygggg4exypy3bhxy6w6x6 -s https://api.nuget.org/v3/index.json
    ```

1. <span data-ttu-id="8076e-103">polecenia DotNet wyświetla wyniki proces publikowania:</span><span class="sxs-lookup"><span data-stu-id="8076e-103">dotnet displays the results of the publishing process:</span></span>

    ```output
    info : Pushing AppLogger.1.0.0.nupkg to 'https://www.nuget.org/api/v2/package'...
    info :   PUT https://www.nuget.org/api/v2/package/
    info :   Created https://www.nuget.org/api/v2/package/ 12620ms
    info : Your package was pushed.
    ```

<span data-ttu-id="8076e-104">Zobacz [wypychania nuget dotnet](/dotnet/core/tools/dotnet-nuget-push).</span><span class="sxs-lookup"><span data-stu-id="8076e-104">See [dotnet nuget push](/dotnet/core/tools/dotnet-nuget-push).</span></span>