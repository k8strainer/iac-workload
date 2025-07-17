Ziel: Vollständig automatisiertes Ausrollen eines neuen GKE Workload Clusters plus Installation zentraler Core Services (Ingress Nginx, Cert Manager …) mit Argo CD – ohne manuelle URL Pflege und ohne Helm.

Verzeichnis Layout

├── k8s
│   ├── apps
│   │   ├── core-services-appset.yaml     #ApplicationSet für CertMan,Ingress 
│   │   └── iac-workload-cluster-app.yaml #Application für Workload Cluster
│   ├── core-services                     #Core-Dienste: CertMan, Ingress
│   │   ├── cert-manager
│   │   │   └── cert-manager.yaml         #All-in-One Manifest
│   │   └── ingress
│   │       └── nginx-ingress.yaml        #All-in-One Manifest
│   ├── root-app.yaml                     #Root-App -> zeigt auf k8s/apps
│   └── workload-cluster-1                #Ressourcen für Workload Cluster
│       ├── 04-gke-workload-cluster.yaml
│       └── 06-postsync-cluster-registration.yaml
└── README.md
