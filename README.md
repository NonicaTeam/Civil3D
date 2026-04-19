# Civ API Docs

Civil3D API documentation for years 2022-2027, powered by Algolia search.

**Live Site:** [CivApiDocs](https://civapidocs.com)

## Features

- Multi-year Civil3D API documentation (2022-2027)
- Instant search across all documentation
- Embeddable search snippet for external websites

## Embeddable Search Snippet

Add a Civil3D API search bar to any website. Copy-paste the full snippet directly into WordPress (Custom HTML block), Webflow, Squarespace, or any HTML page.

**Full snippet (copy-paste ready):**
```html
<!-- DocSearch CSS -->
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/@docsearch/css@3" />

<!-- Search container - place this where you want the search bar -->
<div id="algoliaBar"></div>

<!-- DocSearch JS -->
<script src="https://cdn.jsdelivr.net/npm/@docsearch/js@3"></script>

<script type="text/javascript">
docsearch({
    appId: "8IRYFS0A94",
    apiKey: "f0be2c93fea1bdaf08c557853b8792ab",
    indexName: "civapicom",
    container: "#algoliaBar",
    debug: false,
    transformItems(items) {
        return items.map((item) => {
            const yearContent = item._highlightResult.year.value;

            if (!item._highlightResult || !item._highlightResult.tree_breakdown) {
                return { ...item, content: yearContent };
            }

            let treeBreakdown = item._highlightResult.tree_breakdown.value;
            treeBreakdown = treeBreakdown.replace(/Autodesk\.Civil\./g, "").trim();

            const newContent = treeBreakdown !== "" 
                ? `${yearContent} | ${treeBreakdown}` 
                : yearContent;

            return {
                ...item,
                content: newContent,
            };
        });
    },
    maxResultsPerGroup: 20,
    initialQuery: "2027 ",
})
</script>
```

## Related

- [Civil3D API Docs](https://civapidocs.com/)
- [Revit API Docs](https://revapidocs.com/)

## License

[MIT License + Attribution](license.md) - by [Nonica.io](https://nonica.io)
