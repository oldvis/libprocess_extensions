# Telefact

The class for scraping metadata and images from [Telefact: 1938-1945 by Pictograph Corporation](https://modley-telefact-1939-1945.tumblr.com/).

## Usage

Create a querier for Telefact:

```python
from libquery_extensions import Telefact

directory = "./output/telefact"
querier = Telefact(
    metadata_path=f"{directory}/metadata/metadata.jsonl",
    img_dir=f"{directory}/imgs",
)
```

Query metadata:

```python
base_url = "https://modley-telefact-1939-1945.tumblr.com/post/"
queries = [
    f"{base_url}616877845505064960/rudolf-modley-pictograph",
    f"{base_url}614489066195632128/rudolf-modley-pictograph-corporation",
    f"{base_url}614476957421338624/fridec231938",
]
querier.fetch_metadata(queries=queries)
```

Query images:

```python
querier.fetch_image()
```

## Processed Metadata Schema

Each processed metadata entry is stored as:

```typescript
interface ProcessedMetadataEntry {
    uuid: string
    authors: ['Modley, Rudolf']
    /** Generate with `Telefact-${idInSource}`. */
    displayName: string
    publishDate: {
        year: number
        month: number
        day: number
    }
    viewUrl: string
    downloadUrl: string
    md5?: string
    phash?: string
    resolution?: [number, number]
    fileSize?: number
    languages: ['eng']
    source: {
        name: 'Telefact'
        /** The url where the metadata is collected. */
        url: string
        accessDate: string
    }
}
```
