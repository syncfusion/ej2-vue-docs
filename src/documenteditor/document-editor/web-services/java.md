---
title: "Java web service for Word Processor a.k.a. Document Editor"
component: "DocumentEditor"
description: "Illustrates how to create web service in Java for the server-side dependent functionalities of Word Processor component a.k.a. Document Editor."
---

# Using Java web service in Vue DocumentEditor control

This page illustrates how to create web service in Java for the server-side dependent functionalities of Word Processor component a.k.a. Document Editor. Document Editor depends on server side interaction for below listed operations and it can be written in Java using `syncfusion-ej2-wordprocessor.jar` file.

* Import Word Document
* Paste with formatting
* Restrict Editing
* Spell Check
* Save as file formats other than SFDT and DOCX

## Supported Java versions

Syncfusion Java library supports Java SE 8.0(1.8) or above versions.

## External Jars Required

The following jar files are required to be referenced in your Java application.

1. syncfusion-ej2-wordprocessor

2. syncfusion-docio

3. syncfusion-javahelper

## Download JAR file

The JAR file is available in both [Syncfusion Essential-JS2](https://www.syncfusion.com/downloads/essential-js2) build and maven repository.

### Get JAR file from Syncfusion build

You can get the `syncfusion-ej2-wordprocessor.jar` and its dependent jar files from Syncfusion build installed location.

**Syntax:**
> Jar file: `(installed location)/Syncfusion/Essential Studio/{Platform}/{version}/JarFiles/syncfusion-ej2-wordprocessor-{version}.jar`

**Example:**
> Jar file: `C:/Program Files (x86)/Syncfusion/Essential Studio/JavaScript - EJ2/18.4.0.30/JarFiles/syncfusion-ej2-wordprocessor-18.4.0.30.jar`

You can also get the jar files by installing [file formats controls](https://www.syncfusion.com/sales/products/fileformats?utm_source=ug&utm_medium=listing&utm_campaign=java-word-processor#). You can find the required jars in the build installed location.

**Syntax:**
> Jar file: `(installed location)/Syncfusion/Essential Studio/{Platform}/{version}/JarFiles/syncfusion-ej2-wordprocessor-{version}.jar`

**Example:**
> Jar file: `C:/Program Files (x86)/Syncfusion/Essential Studio/FileFormats/18.4.0.30/JarFiles/syncfusion-ej2-wordprocessor-18.4.0.30.jar`

### Referring JAR from Syncfusion Maven Repository

You can download the jars from the Syncfusion [maven repository](https://jars.syncfusion.com/) to use our artifacts in your projects. It helps to use the Syncfusion Java packages without installing Essential Studio or platform installation to development with Syncfusion controls.

#### Download Syncfusion Java packages

You can easily download the Syncfusion packages for Java via maven repository. Follow the below guidelines to configure as per the tool.

#### Refer the maven repository in build tool

##### Gradle

```java
    repositories {
        maven {
        // Syncfusion maven repository to download the artifacts
        url "https://jars.syncfusion.com/repository/maven-public/"
        }
    }
```

##### Apache Maven

```java
    <repository>
        <id>Syncfusion-Java</id>
        <name>Syncfusion Java repo</name>
        <url>https://jars.syncfusion.com/repository/maven-public/</url>
    </repository>
```

#### Refer the Syncfusion package in your project as the dependency

##### Gradle

```java
    dependencies {
        implementation 'com.syncfusion:syncfusion-ej2-wordprocessor:18.4.0.30'
    }
```

##### Apache Maven

```java
    <dependency>
        <groupId>com.syncfusion</groupId>
        <artifactId>syncfusion-ej2-wordprocessor</artifactId>
        <version>18.4.0.30</version>
    </dependency>
```

This section explains how to create the Java web service for DocumentEditor.

## Importing Word Document

As the Document editor client-side script requires the document in SFDT file format, you can convert the Word documents (.dotx,.docx,.docm,.dot), rich text format documents (.rtf), and text documents (.txt) into SFDT format by using this Web API.

The following example code illustrates how to write a Web API for importing Word documents into Document Editor component.

```java
    @CrossOrigin(origins = "*", allowedHeaders = "*")
    @PostMapping("/api/wordeditor/Import")
    public String uploadFile(@RequestParam("files") MultipartFile file) throws Exception {
        try {
            return WordProcessorHelper.load(file.getInputStream(), FormatType.Docx);
        } catch (Exception e) {
            e.printStackTrace();
            return "{\"sections\":[{\"blocks\":[{\"inlines\":[{\"text\":" + e.getMessage() + "}]}]}]}";
        }
    }
```

## Paste with formatting

This Web API converts the system clipboard data (HTML/RTF) to SFDT format which is required to paste content with formatting.

The following example code illustrates how to write a Web API for paste with formatting.

```java
    @CrossOrigin(origins = "*", allowedHeaders = "*")
    @PostMapping("/api/wordeditor/SystemClipboard")
    public String systemClipboard(@RequestBody CustomParameter param) {
        if (param.content != null && param.content != "") {
            try {
                return  WordProcessorHelper.loadString(param.content, GetFormatType(param.type.toLowerCase()));
            } catch (Exception e) {
                return "";
            }
        }
        return "";
    }

    public class CustomParameter {
        public String content;
        public String type;
        public String getContent() {
            return content;
        }
        public String getType() {
            return type;
        }
        public void setContent(String value) {
            content= value;
        }
        public void setType(String value) {
            type = value;
        }
    }
```

## Restrict editing

This Web API generates hash from the specified password and salt value which is required for restrict editing functionality of Document Editor component.

The following example code illustrates how to write a Web API for restrict editing.

```java
    @CrossOrigin(origins = "*", allowedHeaders = "*")
    @PostMapping("/api/wordeditor/RestrictEditing")
    public String[] restrictEditing(@RequestBody CustomRestrictParameter param) throws Exception {
        if (param.passwordBase64 == "" && param.passwordBase64 == null)
            return null;
        return WordProcessorHelper.computeHash(param.passwordBase64, param.saltBase64, param.spinCount);
    }

    public class CustomRestrictParameter {
        public String passwordBase64;
        public String saltBase64;
        public int spinCount;
        public String getPasswordBase64() {
            return passwordBase64;
        }
        public String getSaltBase64() {
            return saltBase64;
        }
        public int getSpinCount() {
            return spinCount;
        }
        public void setPasswordBase64(String value) {
            passwordBase64= value;
        }
        public void setSaltBase64(String value) {
            saltBase64= value;
        }
        public void setSpinCount(int value) {
            spinCount= value;
        }
    }
```

## Spell Check

Document Editor supports performing spell checking for any input text. You can perform spell checking for the text in Document Editor and it will provide suggestions for the mis-spelled words through dialog and in context menu. Document editor client-side script requires this Web API to show error words and list suggestions in context menu. This Web API returns the json type of spell-checked word which contains details about error words if any and suggestions.

To know more about configure spell check, please check this [link](https://github.com/SyncfusionExamples/EJ2-Document-Editor-Web-Services/tree/master/Java#steps-to-configure-spell-checker).

In controller file, you can configure the spell check files like below:

```java

    List<DictionaryData> spellDictionary;
    String personalDictPath;

    public WordEditorController() throws Exception {

    String jsonFilePath = "src/main/resources/spellcheck.json";
    String jsonContent = new String(Files.readAllBytes(Paths.get(jsonFilePath)), StandardCharsets.UTF_8);
    JsonArray spellDictionaryItems = new Gson().fromJson(jsonContent, JsonArray.class);
    personalDictPath = "src/main/resources/customDict.dic";
    spellDictionary = new ArrayList<DictionaryData>();
    for(int i = 0; i < spellDictionaryItems.size(); i++) {
        JsonObject spellCheckerInfo = spellDictionaryItems.get(i).getAsJsonObject();
        DictionaryData dict = new DictionaryData();

        if(spellCheckerInfo.has("LanguadeID"))
            dict.setLanguadeID(spellCheckerInfo.get("LanguadeID").getAsInt());
        if(spellCheckerInfo.has("DictionaryPath"))
            dict.setDictionaryPath("src/main/resources/"+spellCheckerInfo.get("DictionaryPath").getAsString());
        if(spellCheckerInfo.has("AffixPath"))
            dict.setAffixPath("src/main/resources/"+spellCheckerInfo.get("AffixPath").getAsString());
        spellDictionary.add(dict);
    }

    }

```

Document editor provides options to spell check word by word and spellcheck page by page when loading the documents.

### Spell check word by word

This Web API performs the spell check word by word and return the json which contains information about error words and suggestions if any. By default, spell check word by word is performed in Document editor when enabling spell check in client-side.

The following example code illustrates how to write a Web API for spell check word by word.

```csharp

    @CrossOrigin(origins = "*", allowedHeaders = "*")
    @PostMapping("/api/wordeditor/SpellCheck")
    public String spellCheck(@RequestBody SpellCheckJsonData spellChecker) throws Exception {
        try {
              SpellChecker spellCheck = new SpellChecker(spellDictionary,personalDictPath);
               String data = spellCheck.getSuggestions(spellChecker.languageID, spellChecker.texttoCheck, spellChecker.checkSpelling, spellChecker.checkSuggestion, spellChecker.addWord);
              return data;
        } catch (Exception e) {
            e.printStackTrace();
            return "{\"SpellCollection\":[],\"HasSpellingError\":false,\"Suggestions\":null}";
        }

    }

    public class SpellCheckJsonData {

    @JsonProperty("LanguageID")
    int languageID;
    @JsonProperty("TexttoCheck")
    String texttoCheck;
    @JsonProperty("CheckSpelling")
    boolean checkSpelling;
    @JsonProperty("CheckSuggestion")
    boolean checkSuggestion;
    @JsonProperty("AddWord")
    boolean addWord;

    }
```

### Spell check page by page

This Web API performs the spell check page by page and return the json which contains information about error words and suggestions if any. By [enabling optimized spell check](../../document-editor/spell-check#enableoptimizedspellcheck) in client-side, you can perform spellcheck page by page when loading the documents.

The following example code illustrates how to write a Web API for spell check page by page.

```csharp

    @CrossOrigin(origins = "*", allowedHeaders = "*")
    @PostMapping("/api/wordeditor/SpellCheckByPage")
    public String spellCheckByPage(@RequestBody SpellCheckJsonData spellChecker) throws Exception {
        try {
              SpellChecker spellCheck = new SpellChecker(spellDictionary,personalDictPath);
               String data = spellCheck.checkSpelling(spellChecker.languageID, spellChecker.texttoCheck);
              return data;
        } catch (Exception e) {
            e.printStackTrace();
            return "{\"SpellCollection\":[],\"HasSpellingError\":false,\"Suggestions\":null}";
        }
    }


    public class SpellCheckJsonData {

    @JsonProperty("LanguageID")
    int languageID;
    @JsonProperty("TexttoCheck")
    String texttoCheck;
    @JsonProperty("CheckSpelling")
    boolean checkSpelling;
    @JsonProperty("CheckSuggestion")
    boolean checkSuggestion;
    @JsonProperty("AddWord")
    boolean addWord;

    }
```

## Save

You can configure this API, if you want to save the document in file format other than DOCX and SFDT using server-side. You can save the document in following ways:

### Save

This Web API saves the document in the server machine. You can customize this API to save the document into databases or file servers.

The following example code illustrates how to write a Web API for save document in server-side.

```csharp

    @CrossOrigin(origins = "*", allowedHeaders = "*")
    @PostMapping("/api/wordeditor/Save")
    public void save(@RequestBody SaveParameter data) throws Exception {
        try {
            String name = data.getFileName();
            String format = retrieveFileType(name);
            if (name == null || name.isEmpty()) {
                name = "Document1.docx";
            }
            WordDocument document = WordProcessorHelper.save(data.getContent());
            // Saves the document to server machine file system, you can customize here to save into databases or file servers based on requirement.
            FileOutputStream fileStream = new FileOutputStream(name);
            document.save(fileStream, getWFormatType(format));
            fileStream.close();
            document.close();
        } catch (Exception ex) {
            throw new Exception(ex.getMessage());
        }
    }

    public class SaveParameter {
    private String _content;
    private String _fileName;

    public String getContent() {
        return _content;
    }

    public String setContent(String value) {
        _content = value;
        return value;
    }

    public String getFileName() {
        return _fileName;
    }

    public String setFileName(String value) {
        _fileName = value;
        return value;
    }
    }
    static com.syncfusion.docio.FormatType getWFormatType(String format) throws Exception {

        if (format == null || format.trim().isEmpty())
            throw new Exception("EJ2 WordProcessor does not support this file format.");
        switch (format.toLowerCase()) {
        case ".dotx":
            return com.syncfusion.docio.FormatType.Dotx;
        case ".docm":
            return com.syncfusion.docio.FormatType.Docm;
        case ".dotm":
            return com.syncfusion.docio.FormatType.Dotm;
        case ".docx":
            return com.syncfusion.docio.FormatType.Docx;
        case ".rtf":
            return com.syncfusion.docio.FormatType.Rtf;
        case ".html":
            return com.syncfusion.docio.FormatType.Html;
        case ".txt":
            return com.syncfusion.docio.FormatType.Txt;
        case ".xml":
            return com.syncfusion.docio.FormatType.WordML;
        default:
            throw new Exception("EJ2 WordProcessor does not support this file format.");
        }
    }
```

### ExportSfdt

This Web API converts the SFDT string to required format and returns the document as FileStreamResult to client-side. Using this API, you can save the document in file format other than SFDT and DOCX and download the document in client browser.

The following example code illustrates how to write a Web API for export sfdt.

```csharp
    @CrossOrigin(origins = "*", allowedHeaders = "*")
    @PostMapping("/api/wordeditor/ExportSFDT")
    public ResponseEntity<Resource> exportSFDT(@RequestBody SaveParameter data) throws Exception {
        try {
            String name = data.getFileName();
            String format = retrieveFileType(name);
            if (name == null || name.isEmpty()) {
                name = "Document1.docx";
            }
            WordDocument document = WordProcessorHelper.save(data.getContent());
            return saveDocument(document, format);
        } catch (Exception ex) {
            throw new Exception(ex.getMessage());
        }
    }

    public class SaveParameter {

    private String _content;
    private String _fileName;

    public String getContent() {
        return _content;
    }

    public String setContent(String value) {
        _content = value;
        return value;
    }

    public String getFileName() {
        return _fileName;
    }

    public String setFileName(String value) {
        _fileName = value;
        return value;
    }
    }

    private ResponseEntity<Resource> saveDocument(WordDocument document, String format) throws Exception {
        String contentType = "";
        ByteArrayOutputStream outStream = new ByteArrayOutputStream();
        com.syncfusion.docio.FormatType type = getWFormatType(format);
        switch (type.toString()) {
        case "Rtf":
            contentType = "application/rtf";
            break;
        case "WordML":
            contentType = "application/xml";
            break;
        case "Dotx":
            contentType = "application/vnd.openxmlformats-officedocument.wordprocessingml.template";
            break;
        case "Html":
            contentType = "application/html";
            break;
        }
        document.save(outStream, type);
        ByteArrayResource resource = new ByteArrayResource(outStream.toByteArray());
        outStream.close();
        document.close();

        return ResponseEntity.ok().contentLength(resource.contentLength())
                .contentType(MediaType.parseMediaType(contentType)).body(resource);
    }
```

### Export

This Web API converts the DOCX document to required format and returns the document as FileStreamResult to client-side. Using this API, you can save the document in file format other than SFDT and DOCX and download the document in client browser.

The following example code illustrates how to write a Web API for export.

```csharp

    @CrossOrigin(origins = "*", allowedHeaders = "*")
    @PostMapping("/api/wordeditor/Export")
    public ResponseEntity<Resource> export(@RequestParam("data") MultipartFile data, String fileName) throws Exception {
        try {
            String name = fileName;
            String format = retrieveFileType(name);
            if (name == null || name.isEmpty()) {
                name = "Document1";
            }
            WordDocument document = new WordDocument(data.getInputStream(), com.syncfusion.docio.FormatType.Docx);
            return saveDocument(document, format);
        } catch (Exception ex) {
            throw new Exception(ex.getMessage());
        }
    }

    private ResponseEntity<Resource> saveDocument(WordDocument document, String format) throws Exception {
        String contentType = "";
        ByteArrayOutputStream outStream = new ByteArrayOutputStream();
        com.syncfusion.docio.FormatType type = getWFormatType(format);
        switch (type.toString()) {
        case "Rtf":
            contentType = "application/rtf";
            break;
        case "WordML":
            contentType = "application/xml";
            break;
        case "Dotx":
            contentType = "application/vnd.openxmlformats-officedocument.wordprocessingml.template";
            break;
        case "Html":
            contentType = "application/html";
            break;
        }
        document.save(outStream, type);
        ByteArrayResource resource = new ByteArrayResource(outStream.toByteArray());
        outStream.close();
        document.close();

        return ResponseEntity.ok().contentLength(resource.contentLength())
                .contentType(MediaType.parseMediaType(contentType)).body(resource);
    }


```

>Note: Please refer the [Java Web API example from GitHub](https://github.com/SyncfusionExamples/EJ2-DocumentEditor-WebServices/tree/master/Java).