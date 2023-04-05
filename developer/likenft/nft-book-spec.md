---
description: Based on Metadata best practice
---

# NFT Book Spec

## Background

The NFT Book introduced by Liker Land is designed for publishing ebooks as NFT on LikeCoin chain. Unlike Writing NFT which can be used for content of any length, NFT Book are intended for more traditional ebook, with proper cover and editing.

## ISCN metadata

| key                    | value                                              | description                                                                                                                                        |
| ---------------------- | -------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| contentMetadata        |                                                    |                                                                                                                                                    |
| contentMetadata.url    | {URL for "View content"}                           | The main URL that prepresent the NFT Book. This URL would be used for "View content" button in LikerLand                                           |
| contentMetadata.type   | Book                                               | `Book` is used as type                                                                                                                             |
| contentMetadata.sameAs | \["https://url/book.epub", "https://url/book.pdf"] | Array of other URL representations of the NFT Book. If the URL ends with `.epub` or `.pdf` a special button for viewing would appear in Liker Land |

## NFT Class metadata

Each writing NFT class represent a creative work registered on an ISCN. To allow easier search and collection of all Writing NFTs created by a same creator, nft\_meta\_collection fields would be used. A dynamic API is used as uri to provide dynamic metadata according to mint purchase status.

| key                                        | value               | description                                                                    |
| ------------------------------------------ | ------------------- | ------------------------------------------------------------------------------ |
| name                                       | {name of book}      | Name of the book                                                               |
| symbol                                     | BOOK                | `BOOK` is used as symbol                                                       |
| uri                                        | content hash or URL | If a JSON URL is provided, its content is fetched and used as metadata (merge) |
| metadata                                   |                     |                                                                                |
| metadata.nft\_meta\_collection\_id         | nft\_book           | ID of the NFT Book meta collection                                             |
| metadata.nft\_meta\_collection\_name       | NFT Book            | Name of NFT Book meta collection                                               |
| metadata.nft\_meta\_collection\_descrption | NFT Book            | Description of Writing NFT                                                     |

## Registering via command line

A command line tool and sample is provided for easy minting of NFTs

Please view the [repository](https://github.com/likecoin/iscn-nft-tools/tree/master/mint-nft) for details
