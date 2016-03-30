---
title: "Hello Hugo!"
description: "Saying 'Hello' from Hugo"
date: "2014-09-01"
categories:
  - "example"
  - "hello"
tags:
  - "example"
  - "hugo"
  - "blog"
---

Hello from Hugo! If you're reading this in your browser, good job! The file `content/post/hello-hugo.md` has been
converted into a complete HTML document by Hugo. Isn't that pretty nifty?

A Section
---------

Here's a simple titled section where you can place whatever information you want.

You can use inline HTML if you want, but really there's not much that Markdown can't do.

Showing off with Markdown
-------------------------

A full cheat sheet can be found [here](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)
or through [Google](https://google.com/).

There are some *easy* examples for styling, though. I can't **emphasize** that enough.
Creating [links](https://google.com/) or `inline code` blocks are very straightforward.

```
There are some *easy* examples for styling, though. I can't **emphasize** that enough.
Creating [links](https://google.com/) or `inline code` blocks are very straightforward.
```

Front Matter for Fun
--------------------

This is the meta data for this post. It is located at the top of the `content/post/hello-hugo.md` markdown file.

```
---
title: "Hello Hugo!"
description: "Saying 'Hello' from Hugo"
date: "2014-09-01"
categories:
  - "example"
  - "hello"
tags:
  - "example"
  - "hugo"
  - "blog"
---
```

This section, called 'Front Matter', is what tells Hugo about the content in this file: the `title` of the item, the
`description`, and the `date` it was posted. In our example, we've added two custom bits of data too. The `categories` and
`tags` sections are used in this example for indexing/grouping content. You will learn more about what that means by
examining the code in this example and through reading the Hugo [documentation](http://gohugo.io/overview/introduction).

And here is some Java code to go along
```java
public class JaxbPepXmlTest {

    public static void main(String[] args) throws JAXBException {

        // input file
        String path = "G:\\tmp\\pepxml\\test_data\\interact-20130328_EXQ8_NaNa_SA_HeLa_rep04_06.pep.xml";
        Path p = Paths.get(path).toAbsolutePath();
        File f = new File(p.toString());

        // declaring what to parse

        // run the parser
        JAXBContext ctx = JAXBContext.newInstance(MsmsPipelineAnalysis.class);
        Unmarshaller unmarshaller  = ctx.createUnmarshaller();
        Object unmarshalled = unmarshaller.unmarshal(f);
        MsmsPipelineAnalysis pipelineAnalysis = (MsmsPipelineAnalysis) unmarshalled;


        // use the unmarshalled object
        if (pipelineAnalysis.getMsmsRunSummary().isEmpty()) {
            error("MS/MS run summary was empty!");
        }

        MsmsPipelineAnalysis.MsmsRunSummary run = pipelineAnalysis.getMsmsRunSummary().get(0);
        List<MsmsPipelineAnalysis.MsmsRunSummary.SpectrumQuery> queries = run.getSpectrumQuery();
        if (queries.isEmpty()) {
            error("Spectrum queries table was empty!");
        }

        for (MsmsPipelineAnalysis.MsmsRunSummary.SpectrumQuery query : queries) {
            List<MsmsPipelineAnalysis.MsmsRunSummary.SpectrumQuery.SearchResult> searchResult = query.getSearchResult();
            if (searchResult.isEmpty()) {
                error(String.format("Search RESULT was empty for query #%d [spec id: %s]", query.getIndex(), query.getSpectrum()));
            }
            MsmsPipelineAnalysis.MsmsRunSummary.SpectrumQuery.SearchResult result = searchResult.get(0);
            List<MsmsPipelineAnalysis.MsmsRunSummary.SpectrumQuery.SearchResult.SearchHit> searchHit = result.getSearchHit();
            if (searchHit.isEmpty()) {
                error(String.format("Search HIT was empty for query #%d [spec id: %s]", query.getIndex(), query.getSpectrum()));
            }
            MsmsPipelineAnalysis.MsmsRunSummary.SpectrumQuery.SearchResult.SearchHit firstHit = searchHit.get(0);
            MsmsPipelineAnalysis.MsmsRunSummary.SpectrumQuery.SearchResult.SearchHit.ModificationInfo mods = firstHit.getModificationInfo();

            if (mods != null) {
                System.out.printf("mod info is not null for query #%d [spec id: %s]\n", query.getIndex(), query.getSpectrum());
                if (!mods.getModAminoacidMass().isEmpty()) {
                    int x = 1;
                }
                if (mods.getModCtermMass() != null) {
                    int y = 1;
                }
                if (mods.getModNtermMass() != null) {
                    int z = 1;
                }
            }
        }


        int a = 1;
    }


    private static void error(String msg) {
        System.err.println(msg);
        System.exit(1);
    }
}
```
