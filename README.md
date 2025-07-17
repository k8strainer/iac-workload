Ziel: Vollständig automatisiertes Ausrollen eines neuen GKE Workload Clusters plus Installation zentraler Core Services (Ingress Nginx, Cert Manager …) mit Argo CD – ohne manuelle URL Pflege und ohne Helm.

Verzeichnis Layout

repo/
└─ k8s/
   ├─ root-app.yaml                   # Root‑Application (App of Apps)
   ├─ apps/                           # <– *nur* Application / ApplicationSet YAMLs!
   │   ├─ workload-app.yaml           # Child Application – erstellt Cluster  (Wave 0)
   │   └─ core-services-appset.yaml   # ApplicationSet  – rollt Core Services (Wave 1) aus
   ├─ workload-cluster-1/             # CAPI Manifeste (Cluster, MachinePool, Hook …)
   │   ├─ 04-gke-workload-cluster.yaml
   │   └─ 06-postsync-cluster-registration.yaml
   └─ core-services/                  # Reine YAML Manifeste
       ├─ cert-manager/
       │   └─ cert-manager-v1.17.2.yaml
       └─ ingress/
           └─ nginx-ingress-1.11.5.yaml
