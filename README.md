# Interview Devcontainer

## GitHub Codespaces / Devcontainer

This repo is configured with a [devcontainer][]. To use the devcontainer, install
the [VSCode Remote extension pack][vscode-remote] and follow the instructions or
open GitHub Codespaces from [GitHub.com][github].

## Container Services

The devcontainer is configured with the following services.

| Service                    | Env var / URL                                            |
| -------------------------- | -------------------------------------------------------- |
| [CockroachDB][cockroachdb] | `DATABASE_URL=postgres://root@cockroach:26257/defaultdb` |
| [Kafka UI][kafka-ui]       | http://localhost:34197                                   |
| [Kafka][kafka]             | `KAFKA_BOOTSTRAP_SERVER=kafka:9092`                      |
| [Zookeeper][zookeeper]     | `zookeeper:2181`                                         |

## Sample Datasets

Sample data is available under [`data/`](data/README.md). Additional datasets may be downloaded from the [Azure Databricks sample datasets][databricks-data] page.

[cockroachdb]: https://www.cockroachlabs.com
[databricks-data]: https://learn.microsoft.com/en-us/azure/databricks/dbfs/databricks-datasets
[devcontainer]: https://containers.dev
[github]: https://github.com
[kafka-ui]: https://github.com/provectus/kafka-ui
[kafka]: https://kafka.apache.org
[vscode-remote]: https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.vscode-remote-extensionpack
[zookeeper]: https://zookeeper.apache.org
