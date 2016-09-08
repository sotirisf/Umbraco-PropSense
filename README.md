# Umbraco-PropSense
Not using strongly-typed models for your Umbraco views / templates / macros but still need Intellisense? If so, then just copy those templates in your App_Code directory and right-click-"Run Custom Tool" on UmbracoData.tt from within Visual Studio. 

This will generate a set of classes under the namespace DotSee.PropSense with constants that correspond to document property aliases.

Here's an example of such a generated class for the document type alias "dContentSliderItem":

```csharp
public static class Psn_dContentSliderItem
	{
		public const string TypeName = "dContentSliderItem";
		public const string internalLink = "internalLink";
		public const string externalLink = "externalLink";
		public const string content = "content";
		public const string buttonText = "buttonText";
		public const string image = "image";
		public const string imagePosition = "imagePosition";
	}
```

All classes get the prefix "Psn_" for easy Intellisense and their properties correspond to document property aliases (compositions included). So, next time you need to do something like:

```csharp
someNode.GetPropertyValue("internalLink")
```

you can instead do:

```csharp
someNode.GetPropertyValue(Psn_dContentSliderItem.internalLink)
```

Yes, it's longer and it doesn't exactly respect conventions (if the alias starts with a lowercase letter, then the property will also start with lowercase) but it gives you intellisense, and that's what you need to save time spent on typos and misspellings.

As you can see, there's also the TypeName property which gives you the document type alias in case you need it somewhere.

Please remember to re-run this whenever you make changes to document properties.

### Other notes
Although this is under my account, it was originally developed by [George J. Capnias](https://github.com/gcapnias) and is posted here with his permission. Idea and some testing were mine. Thanks! 
