# Reference

## Base URL

Production: `https://mainnet-node.like.co`
Testnet: `https://node.testnet.like.co`

## Ranking API

`/likechain/likenft/v1/ranking`

### Request Params

| Param            | Example                                            | Description                                               |
| ---              | ---                                                | ---                                                       |
| creator          | `like13f4glvg80zvfrrs7utft5p68pct4mcq7t5atf6`      | The current owner of the ISCN                             |
| collector        | `like1vymrc5dxlfwff30m03prwlu08ql4vudn4lue8u`      | The current owner of NFT                                  |
| type             | `CreativeWork`                                     | The `contentMetadata.@type` field in ISCN                 |
| stakeholder_id   | `did:like:1w6es6du93xmhms60gwwtczr2p2h4cdm8r7kc0f` | The `stakeholders.entity.@id` field in ISCN               |
| stakeholder_name | `kin`                                              | The `stakeholders.entity.name` field in ISCN              |
| after            | `1659283200`                                       | Get NFT class created after this UNIX second timestamp    |
| before           | `1659801600`                                       | Get NFT class created before this UNIX second timestamp   |
| include_owner    | `true`                                             | Whether to include owner of ISCN when counting sold_count |
| ignore_list      | `like17m4vwrnhjmd20uu7tst7nv0kap6ee7js69jfrs`      | The addresses to ignore when counting sold count          |
| limit            | `20`                                               | The limit of response. Default & max: 100                 |

Result is order by the number of NFTs not owned by creator nor `ignore_list`

### Example Response

`/likechain/likenft/v1/ranking?ignore_list=like17m4vwrnhjmd20uu7tst7nv0kap6ee7js69jfrs&limit=1`

```json
{
  "classes": [
    {
      "id": "likenft1yhsps5l8tmeuy9y7k0rjpx97cl67cjkjnzkycecw5xrvjjp6c5yqz0ttmc",
      "name": "Writing NFT - 分散式出版 DePub 的發展路徑，NFT 從移民到原住民",
      "description": "...",
      "symbol": "WRITING",
      "uri": "https://api.like.co/likernft/metadata?iscn_id=iscn%3A%2F%2Flikecoin-chain%2FIKI9PueuJiOsYvhN6z9jPJIm3UGMh17BQ3tEwEzslQo%2F3",
      "uri_hash": "",
      "config": {
        "burnable": false,
        "max_supply": "0",
        "blind_box_config": null
      },
      "metadata": {
        "url": "https://ckxpress.com/nft-immigrant-to-native/",
        "name": "分散式出版 DePub 的發展路徑，NFT 從移民到原住民",
        "@type": "Article",
        "image": "ar://_GJD1gNuIqXicYNWce__4B8Qqg5tN8FBRSUCXR8kuJE",
        "version": 1,
        "@context": "http://schema.org/",
        "keywords": "DePub,LikeCoin,nft,Numbers",
        "usageInfo": "",
        "description": "...",
        "nft_meta_collection_id": "likerland_writing_nft",
        "nft_meta_collection_name": "Writing NFT",
        "nft_meta_collection_descrption": "Writing NFT by Liker Land"
      },
      "parent": {
        "type": "ISCN",
        "iscn_id_prefix": "iscn://likecoin-chain/IKI9PueuJiOsYvhN6z9jPJIm3UGMh17BQ3tEwEzslQo",
        "account": ""
      },
      "price": 0,
      "created_at": "2022-08-01T06:33:21Z",
      "sold_count": 171
    }
  ],
  "pagination": {
    "count": 1
  }
}

```

*Note: Currently only like.co API can report the latest price. `price` in the response is always 0. Please refer to like.co API documentation for price information*

### Example UI

https://lancatlin.github.io/likenft-ranking/ 

[source code](https://github.com/lancatlin/likenft-ranking)

---

## Social Graph API

### Get Collectors

`/likechain/likenft/v1/collector`

| Param       | Example                                       | Description                             |
| ---         | ---                                           | ---                                     |
| **creator** | `like13f4glvg80zvfrrs7utft5p68pct4mcq7t5atf6` | Required. Account address of ISCN owner |
| limit       | `100`                                         | Max: 100                                |
| offset      | `200`                                         | Offset of response                      |


### Get Creators

`/likechain/likenft/v1/creator`

| Param         | Example                                       | Description                            |
| ---           | ---                                           | ---                                    |
| **collector** | `like13f4glvg80zvfrrs7utft5p68pct4mcq7t5atf6` | Required. Account address of NFT owner |
| limit         | `100`                                         | Max: 100                               |
| offset        | `200`                                         | Offset of response                     |

Result is order by count of NFT collections.

### Example Response

`/likechain/likenft/v1/collector?creator=like13f4glvg80zvfrrs7utft5p68pct4mcq7t5atf6`

```json
{
  "collectors": [
    {
      "account": "like17m4vwrnhjmd20uu7tst7nv0kap6ee7js69jfrs",             // The like.co NFT sales API wallet
      "count": 2928,
      "collections": [
        {
          "iscn_id_prefix": "iscn://likecoin-chain/IKI9PueuJiOsYvhN6z9jPJIm3UGMh17BQ3tEwEzslQo",
          "class_id": "likenft1yhsps5l8tmeuy9y7k0rjpx97cl67cjkjnzkycecw5xrvjjp6c5yqz0ttmc",
          "count": 443
        },
        {
          "iscn_id_prefix": "iscn://likecoin-chain/IKI9PueuJiOsYvhN6z9jPJIm3UGMh17BQ3tEwEzslQo",
          "class_id": "likenft1yzdfkf4fjjekqjmxen0czy5eyufapfrx5y3nd6d7wd6hmyy6zt3sk7ak4z",
          "count": 500
        },
        {
          "iscn_id_prefix": "iscn://likecoin-chain/OImbeoC6JTlEJrjVOJXAj4rF5uS04vuRGbittFGyQbc",
          "class_id": "likenft1h9efvdvj5m275w8sr2u0jsme2xlmpfexjp802ckda3fvuncw95tsnq2c7u",
          "count": 492
        },
        {
          "iscn_id_prefix": "iscn://likecoin-chain/Tz4l66fBAgEMk5IyEJ4_N0FBj2NjLCse3Uqnm8VxR-8",
          "class_id": "likenft1g0652jc6fns73r5ru6pwp6djp99975em576px88wxau7hrmn2d5qf06zs4",
          "count": 500
        },
        {
          "iscn_id_prefix": "iscn://likecoin-chain/Tz4l66fBAgEMk5IyEJ4_N0FBj2NjLCse3Uqnm8VxR-8",
          "class_id": "likenft1yhxut65wavj2jykq07xtm66dnmn75dm5y0tgq8f49azs3lff7ngqrw7kv6",
          "count": 500
        },
        {
          "iscn_id_prefix": "iscn://likecoin-chain/Tz4l66fBAgEMk5IyEJ4_N0FBj2NjLCse3Uqnm8VxR-8",
          "class_id": "likenft1ztyc5usfn36r2uuza86waa7xn9j7r8xjzagtpcesj3p2t7mmj9kssqlxwe",
          "count": 493
        }
      ]
    },
    {
      "account": "like126qel5qhcxnxy2nd0s43pjp2aqujnp60jeg27l",
      "count": 3,
      "collections": [
        {
          "iscn_id_prefix": "iscn://likecoin-chain/IKI9PueuJiOsYvhN6z9jPJIm3UGMh17BQ3tEwEzslQo",
          "class_id": "likenft1yhsps5l8tmeuy9y7k0rjpx97cl67cjkjnzkycecw5xrvjjp6c5yqz0ttmc",
          "count": 1
        },
        {
          "iscn_id_prefix": "iscn://likecoin-chain/OImbeoC6JTlEJrjVOJXAj4rF5uS04vuRGbittFGyQbc",
          "class_id": "likenft1h9efvdvj5m275w8sr2u0jsme2xlmpfexjp802ckda3fvuncw95tsnq2c7u",
          "count": 1
        },
        {
          "iscn_id_prefix": "iscn://likecoin-chain/Tz4l66fBAgEMk5IyEJ4_N0FBj2NjLCse3Uqnm8VxR-8",
          "class_id": "likenft1ztyc5usfn36r2uuza86waa7xn9j7r8xjzagtpcesj3p2t7mmj9kssqlxwe",
          "count": 1
        }
      ]
    },
    {
      "account": "like18q3dzavq7c6njw92344rf8ejpyqxqwzvhz9th5",
      "count": 3,
      "collections": [
        {
          "iscn_id_prefix": "iscn://likecoin-chain/IKI9PueuJiOsYvhN6z9jPJIm3UGMh17BQ3tEwEzslQo",
          "class_id": "likenft1yhsps5l8tmeuy9y7k0rjpx97cl67cjkjnzkycecw5xrvjjp6c5yqz0ttmc",
          "count": 3
        }
      ]
    }
  ],
  "pagination": {
    "count": 3
  }
}
```

### Example UI

https://lancatlin.github.io/likenft-social-graph/ 

[source code](https://github.com/lancatlin/likenft-social-graph)

