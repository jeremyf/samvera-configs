A little repository to help ease the bandwidth reality of the interaction
between:

*   [solr_wrapper][solr_wrapper]
*   [fcrepo_wrapper][fcrepo_wrapper]
*   [engine_cart][engine_cart]

## Why Use It?

Out of the box, development environments that use the above three gems (see
[Hyrax][hyrax]), will download SOLR and FCRepo zip files into a tmp directory
then unzip them inside a tmp directory in the .internal_test_app that EngineCart
generates.

This configuration then forces a download of those resources if:

1) You rebuild your EngineCart created internal_test_app
2) SOLR releases a new version
3) FCRepo releases a new version

This repository helps to clarify the configuration of those services and to
provide a central place for those downloads.

## About the Directories

Below is the top level directory tree of this repository.

```
.
├── README.md
├── downloads
├── instances
├── solr
├── wrapper_configs
└── zips
```

The `./wrapper_cofigs` are amended copies of what [Hyrax][hyrax]'s engine_cart
build generates. They are constructed with absolute paths (to this repository
as installed on jeremyf's machine).

The `./downloads` and `./zips` directory are where we end up storing:

*   Zipped version of the downloaded files
*   JAR files to run fcrepo


The `./solr` directory contains the SOLR configuration that I copied from my
.internal_test_app Hyrax implementation.

## Tell Me More

Please note, this is the configuration that I have tested for my permutations.
What I have found is I am no longer downloading Solr with each time I start up
my Hyrax instance.

I do, however, need to specify the `--config` option for my `solr_wrapper` and
`fcrepo_wrapper` commands:

*   `solr_wrapper --config ~/git/samvera-configs/wrapper_configs/solr_wrapper_test.yml`
*   `fcrepo_wrapper_test --config ~/git/samvera-configs/wrapper_configs/fcrepo_wrapper_test.yml`

Yes, in an ideal world I'd leverage Docker instances. But that is not something
in which I'm looking to develop/implement. Instead, I figured I would try to
develop a better understanding of two core components of Samvera. And from that
understanding I hope to share it with others.

As always pull requests are welcome.

[engine_cart]:https://github.com/cbeer/engine_cart
[fcrepo_wrapper]:https://github.com/cbeer/fcrepo_wrapper
[hyrax]:https://github.com/samvera/hyrax
[solr_wrapper]:https://github.com/cbeer/solr_wrapper
