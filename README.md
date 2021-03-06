# ASP.NET Markdown

[![Build status](https://ci.appveyor.com/api/projects/status/h7gvev4ogigfgjx0?svg=true)](https://ci.appveyor.com/project/velyo/aspnet-markdown)

ASP.NET Markdown control to embed and render markdown content in ASP.NET web forms application.  
The control has built-in simple configurable architecture to provide and easy way to change and configure the markdown engine and markdown resource loading.

## Features

- Embedded markdown content inside the control;
- Configurable markdown engine;
- Configurable markdown content provider;

The control can use an embedded markdown inside the control content on the page.

The external markdown resources are loaded by MarkdownProvider implementation.  
When using MarkdownProvider to load an external markdown resource the Path property of control is used to locate the resource.  
Default MarkdownProvider is using the Path value to look for a resources located under the application root.  
For example:
```
<velyo:MarkdownContent ID="sample2" runat="server" Path="~/docs/page2.md">
```
will try to load the resource from file page2.md placed in docs sub-folder of the application root.  
By configuring the current [MarkdownProvider](/src/Velyo.AspNet.Markdown/MarkdownProvider.cs) ``` MarkdownProvider.Current``` control can use different markdown resource sources (files, database etc.).

The control comes with embedded (default) engine using MarkdownSharp [https://github.com/hey-red/Markdown].  
By creating your own implementation of [MarkdownEngine](/src/Velyo.AspNet.Markdown/MarkdownEngine.cs) and set it to ```MarkdownEngine.Current``` you can configure control to use other markdown engine of your choice.

## Getting Started

To install AspNet Markdown Control, run the following command in the Package Manager Console
```
PM> Install-Package Velyo.AspNet.Markdown
```
After install a new ASP.NET tag prefix will be registered in your web.config
```xml
<add assembly="Velyo.AspNet.Markdown" namespace="Velyo.AspNet.Markdown" tagPrefix="velyo" />
```

You can just add the control to your ASP.NET WebForms page with some embedded markdown content like:
```aspnet
    <velyo:MarkdownContent ID="sample1"  runat="server">
# ASP.NET Markdown

ASP.NET Markdown control to embed and render markdown content in your ASP.NET application.

## Features


## Contribute

Check out the [contribution guidelines](https://github.com/velyo/aspnet-markdown/blob/master/CONTRIBUTING.md) if you want to contribute to this project.

## License

[MIT](https://github.com/velyo/aspnet-markdown/blob/master/LICENSE)

    </velyo:MarkdownContent>
```
Please note there is no line indent in the markdown content in order the markdown engine to be able to process it.  
If you would like to have nice formatted page content, you can use the Indent property of the control in order to help markdown engine to trip down the format indent.
```
<velyo:MarkdownContent ID="sample1"  runat="server" Indent="4">
```

Samples of how to use the control can be found in Velyo.AspNet.Markdown.Samples web application.

## Contribute

Check out the [contribution guidelines](https://github.com/velyo/aspnet-markdown/blob/master/CONTRIBUTING.md) if you want to contribute to this project.

## License

[MIT](https://github.com/velyo/aspnet-markdown/blob/master/LICENSE)
