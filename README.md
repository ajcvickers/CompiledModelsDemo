# CompiledModelsDemo

1. Run the benchemark
2. Compile a model - `dotnet ef dbcontext optimize --output-dir MyCompiledModels --namespace MyCompiledModels`
3. Update OnConfiguring to use the compiled model
4. Comment out the caching in `BlogsContextModel`:

```C#
public static IModel Instance
{
    get
    {
        //if (_instance == null)
        {
            _instance = new BlogsContextModel();
            _instance.Initialize();
            _instance.Customize();
        }
        
        return _instance;
    }
}
```

5. Run benchmark again
