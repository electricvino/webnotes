Popular tools are [[Flux]] and [[ArgoCD]]

When deciding between Argo CD and Flux, consider the following key factors:

|                                     |                                                                                 |                                                                                     |
| ----------------------------------- | ------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| **Criteria**                        | **ArgoCD**                                                                      | **Flux**                                                                            |
| **Synchronization**                 | Global sync interval. Can optionally just diff. Supports flexible Sync Windows. | Per app sync interval. Always discards cluster changes. No support for Sync windows |
| **Architecture**                    | Standalone application with built-in UI                                         | Modular set of controllers within Kubernetes                                        |
| **Application Management**          | Supports ApplicationSets for managing multiple apps                             | Utilizes Helm and Kustomize, requires extra tooling                                 |
| **Web UI**                          | Comprehensive and user-friendly                                                 | Primarily CLI-based; limited visualization via Weave GitOps                         |
| **RBAC**                            | Custom RBAC system with granular controls                                       | Relies on Kubernetes-native RBAC                                                    |
| **Installation**                    | Flexible, YAML-based configuration                                              | Streamlined with automated bootstrapping                                            |
| **Corporate support and community** | Strong community and corporate backing                                          | Uncertain future post-Weaveworks shutdown                                           |

Here are a few key considerations when making the choice between Argo CD and Flux:

- **User interface**: Teams preferring a visual interface should lean towards Argo CD for its robust web UI.
- **Scalability and complexity**: For managing complex deployments, Argo CD’s ApplicationSets provide a streamlined approach, whereas Flux requires additional scripting.
- **Security requirements**: If granular control over permissions is critical, Argo CD’s custom RBAC offers more flexibility.
- **Ease of setup**: Beginners might find Flux easier to start with due to its automated bootstrapping.
- **Future stability**: Consider the potential impact of Weaveworks’ shutdown on Flux’s future updates and community support.