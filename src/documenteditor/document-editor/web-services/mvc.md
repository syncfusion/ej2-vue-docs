---
title: "DocumentEditor web services"
component: "DocumentEditor"
description: "Learn how to create web service in ASP.NET MVC platform for Import, RestrictEditing, Paste with formatting and Spell check."
---

# Creating DocumentEditor web service in ASP.NET MVC

DocumentEditor depends on server side interaction for below listed operations can be written in ASP.NET MVC using [Syncfusion.EJ2.WordEditor.AspNet.Mvc5](https://www.nuget.org/packages/Syncfusion.EJ2.WordEditor.AspNet.Mvc5) or [Syncfusion.EJ2.WordEditor.AspNet.Mvc4](https://www.nuget.org/packages/Syncfusion.EJ2.WordEditor.AspNet.Mvc4).

* Import Word Document
* Paste with formatting
* Restrict Editing
* Spell Check
* Save as file formats other than SFDT and DOCX

This section explains how to create the service for DocumentEditor in ASP.NET MVC.

## Importing Word Document

As the Document editor client-side script requires the document in SFDT file format, you can convert the Word documents (.dotx,.docx,.docm,.dot,.doc), rich text format documents (.rtf), and text documents (.txt) into SFDT format by using this Web API.

The following example code illustrates how to write a Web API for importing Word documents into Document Editor component.

```csharp
    [HttpPost]
    [EnableCors("*", "*", "*")]
    [Route("Import")]
    public HttpResponseMessage Import()
    {
        if (HttpContext.Current.Request.Files.Count == 0)
            return null;

        HttpPostedFile file = HttpContext.Current.Request.Files[0];
        int index = file.FileName.LastIndexOf('.');
        string type = index > -1 && index < file.FileName.Length - 1 ?
            file.FileName.Substring(index) : ".docx";
        Stream stream = file.InputStream;
        stream.Position = 0;

        EJ2WordDocument document = EJ2WordDocument.Load(stream, GetFormatType(type.ToLower()));
        string json = Newtonsoft.Json.JsonConvert.SerializeObject(document);
        document.Dispose();
        return new HttpResponseMessage() { Content = new StringContent(json) };
    }
```

## Paste with formatting

This Web API converts the system clipboard data (HTML/RTF) to SFDT format which is required to paste content with formatting.

The following example code illustrates how to write a Web API for paste with formatting.

```csharp
    [HttpPost]
    [EnableCors("*", "*", "*")]
    [Route("SystemClipboard")]
    public HttpResponseMessage SystemClipboard([FromBody]CustomParameter param)
    {
        if (param.content != null && param.content != "")
        {
            try
            {
                Syncfusion.EJ2.DocumentEditor.WordDocument document = Syncfusion.EJ2.DocumentEditor.WordDocument.LoadString(param.content, GetFormatType(param.type.ToLower()));
                string json = Newtonsoft.Json.JsonConvert.SerializeObject(document);
                document.Dispose();
                return new HttpResponseMessage() { Content = new StringContent(json) };
            }
            catch (Exception)
            {
                return new HttpResponseMessage() { Content = new StringContent("") };
            }

        }
        return new HttpResponseMessage() { Content = new StringContent("") };
    }

    public class CustomParameter
    {
        public string content { get; set; }
        public string type { get; set; }
    }
```

## Restrict editing

This Web API generates hash from the specified password and salt value which is required for restrict editing functionality of Document Editor component.

The following example code illustrates how to write a Web API for restrict editing.

```csharp
    [HttpPost]
    [EnableCors("*", "*", "*")]
    [Route("RestrictEditing")]
    public string[] RestrictEditing([FromBody]CustomRestrictParameter param)
    {
        if (param.passwordBase64 == "" && param.passwordBase64 == null)
            return null;
        return Syncfusion.EJ2.DocumentEditor.WordDocument.ComputeHash(param.passwordBase64, param.saltBase64, param.spinCount);
    }

    public class CustomRestrictParameter
    {
        public string passwordBase64 { get; set; }
        public string saltBase64 { get; set; }
        public int spinCount { get; set; }
    }
```

## Spell Check

Document Editor supports performing spell checking for any input text. You can perform spell checking for the text in Document Editor and it will provide suggestions for the mis-spelled words through dialog and in context menu. Document editor client-side script requires this Web API to show error words and list suggestions in context menu. This Web API returns the json type of spell-checked word which contains details about error words if any and suggestions.

To know more about configure spell check, please check this [link](https://github.com/SyncfusionExamples/EJ2-Document-Editor-Web-Services/tree/master/ASP.NET%20MVC#steps-to-configure-spell-checker).

In `Global.asax.cs` file, you can configure the spell check files like below:

```csharp
        internal static List<DictionaryData> spellDictCollection;
        internal static string path;
        internal static string personalDictPath;
        protected void Application_Start()
        {
            GlobalConfiguration.Configure(WebApiConfig.Register);
            //check the spell check dictionary path environment variable value and assign default data folder
            //if it is null.
            string path = HostingEnvironment.MapPath("\\App_Data\\");
            //Set the default spellcheck.json file if the json filename is empty.
            string jsonFileName = HostingEnvironment.MapPath("\\App_Data\\spellcheck.json");
            if (System.IO.File.Exists(jsonFileName))
            {
                string jsonImport = System.IO.File.ReadAllText(jsonFileName);
                List<DictionaryData> spellChecks = JsonConvert.DeserializeObject<List<DictionaryData>>(jsonImport);
                spellDictCollection = new List<DictionaryData>();
                //construct the dictionary file path using customer provided path and dictionary name
                foreach (var spellCheck in spellChecks)
                {
                    spellDictCollection.Add(new DictionaryData(spellCheck.LanguadeID, Path.Combine(path, spellCheck.DictionaryPath), Path.Combine(path, spellCheck.AffixPath)));
                    personalDictPath = Path.Combine(path, spellCheck.PersonalDictPath);
                }
            }
        }

```

Document editor provides options to spell check word by word and spellcheck page by page when loading the documents.

### Spell check word by word

This Web API performs the spell check word by word and return the json which contains information about error words and suggestions if any. By default, spell check word by word is performed in Document editor when enabling spell check in client-side.

The following example code illustrates how to write a Web API for spell check word by word.

```csharp
    [HttpPost]
    [EnableCors("*", "*", "*")]
    [Route("SpellCheck")]
    public HttpResponseMessage SpellCheck([FromBody] SpellCheckJsonData spellChecker)
    {
       try
        {
            SpellChecker spellCheck = new SpellChecker(spellDictionary, personalDictPath);
            spellCheck.GetSuggestions(spellChecker.LanguageID, spellChecker.TexttoCheck, spellChecker.CheckSpelling, spellChecker.CheckSuggestion, spellChecker.AddWord);
            string json = Newtonsoft.Json.JsonConvert.SerializeObject(spellCheck);
            return new HttpResponseMessage() { Content = new StringContent(json) };
        }
        catch
        {
            return new HttpResponseMessage() { Content = new StringContent("{\"SpellCollection\":[],\"HasSpellingError\":false,\"Suggestions\":null}") };
        }
    }

    public class SpellCheckJsonData
    {
        public int LanguageID { get; set; }
        public string TexttoCheck { get; set; }
        public bool CheckSpelling { get; set; }
        public bool CheckSuggestion { get; set; }
        public bool AddWord { get; set; }
    }
```

### Spell check page by page

This Web API performs the spell check page by page and return the json which contains information about error words and suggestions if any. By [enabling optimized spell check](../../document-editor/spell-check#enableoptimizedspellcheck) in client-side, you can perform spellcheck page by page when loading the documents.

The following example code illustrates how to write a Web API for spell check page by page.

```csharp
    [HttpPost]
    [EnableCors("*", "*", "*")]
    [Route("SpellCheckByPage")]
    public HttpResponseMessage SpellCheckByPage([FromBody] SpellCheckJsonData spellChecker)
    {
        try
        {
            SpellChecker spellCheck = new SpellChecker(spellDictionary, personalDictPath);
            spellCheck.CheckSpelling(spellChecker.LanguageID, spellChecker.TexttoCheck);
            string json = Newtonsoft.Json.JsonConvert.SerializeObject(spellCheck);
            return new HttpResponseMessage() { Content = new StringContent(json) };
        }
        catch
        {
            return new HttpResponseMessage() { Content = new StringContent("{\"SpellCollection\":[],\"HasSpellingError\":false,\"Suggestions\":null}") };
        }
    }

    public class SpellCheckJsonData
    {
        public int LanguageID { get; set; }
        public string TexttoCheck { get; set; }
        public bool CheckSpelling { get; set; }
        public bool CheckSuggestion { get; set; }
        public bool AddWord { get; set; }
    }
```

## Save

You can configure this API, if you want to save the document in file format other than DOCX and SFDT using server-side. You can save the document in following ways:

### Save

This Web API saves the document in the server machine. You can customize this API to save the document into databases or file servers.

The following example code illustrates how to write a Web API for save document in server-side.

```csharp
        [HttpPost]
        [EnableCors("AllowAllOrigins")]
        [Route("Save")]
        public void Save([FromBody] SaveParameter data)
        {
            string name = data.FileName;
            string format = RetrieveFileType(name);
            if (string.IsNullOrEmpty(name))
            {
                name = "Document1.doc";
            }
            WDocument document = WordDocument.Save(data.Content);
            // Saves the document to server machine file system, you can customize here to save into databases or file servers based on requirement.
            FileStream fileStream = new FileStream(name, FileMode.OpenOrCreate, FileAccess.ReadWrite);
            document.Save(fileStream, GetWFormatType(format));
            document.Close();
            fileStream.Close();
        }

        public class SaveParameter
        {
            public string Content { get; set; }
            public string FileName { get; set; }
        }
```

### ExportSfdt

This Web API converts the SFDT string to required format and returns the document as FileStreamResult to client-side. Using this API, you can save the document in file format other than SFDT and DOCX and download the document in client browser.

The following example code illustrates how to write a Web API for export sfdt.

```csharp

        [HttpPost]
        [EnableCors("AllowAllOrigins")]
        [Route("ExportSFDT")]
        public FileStreamResult ExportSFDT([FromBody] SaveParameter data)
        {
            string name = data.FileName;
            string format = RetrieveFileType(name);
            if (string.IsNullOrEmpty(name))
            {
                name = "Document1.doc";
            }
            WDocument document = WordDocument.Save(data.Content);
            return SaveDocument(document, format, name);
        }

        public class SaveParameter
        {
            public string Content { get; set; }
            public string FileName { get; set; }
        }

         private FileStreamResult SaveDocument(WDocument document, string format, string fileName)
        {
            Stream stream = new MemoryStream();
            string contentType = "";
            if (format == ".pdf")
            {
                contentType = "application/pdf";
            }
            else
            {
                WFormatType type = GetWFormatType(format);
                switch (type)
                {
                    case WFormatType.Rtf:
                        contentType = "application/rtf";
                        break;
                    case WFormatType.WordML:
                        contentType = "application/xml";
                        break;
                    case WFormatType.Html:
                        contentType = "application/html";
                        break;
                    case WFormatType.Dotx:
                        contentType = "application/vnd.openxmlformats-officedocument.wordprocessingml.template";
                        break;
                    case WFormatType.Doc:
                        contentType = "application/msword";
                        break;
                    case WFormatType.Dot:
                        contentType = "application/msword";
                        break;
                }
                document.Save(stream, type);
            }
            document.Close();
            stream.Position = 0;
            return new FileStreamResult(stream, contentType)
            {
                FileDownloadName = fileName
            };
        }
```

### Export

This Web API converts the DOCX document to required format and returns the document as FileStreamResult to client-side. Using this API, you can save the document in file format other than SFDT and DOCX and download the document in client browser.

The following example code illustrates how to write a Web API for export.

```csharp


        [HttpPost]
        [EnableCors("AllowAllOrigins")]
        [Route("Export")]
        public FileStreamResult Export(IFormCollection data)
        {
            if (data.Files.Count == 0)
                return null;
            string fileName = this.GetValue(data, "filename");
            string name = fileName;
            string format = RetrieveFileType(name);
            if (string.IsNullOrEmpty(name))
            {
                name = "Document1";
            }
            WDocument document = this.GetDocument(data);
            return SaveDocument(document, format, fileName);
        }

        private string RetrieveFileType(string name)
        {
            int index = name.LastIndexOf('.');
            string format = index > -1 && index < name.Length - 1 ?
                name.Substring(index) : ".doc";
            return format;
        }

        private string GetValue(IFormCollection data, string key)
        {
            if (data.ContainsKey(key))
            {
                string[] values = data[key];
                if (values.Length > 0)
                {
                    return values[0];
                }
            }
            return "";
        }


```

>Note: Please refer the [ASP.NET MVC Web API sample](https://github.com/SyncfusionExamples/EJ2-DocumentEditor-WebServices/tree/master/ASP.NET%20MVC).