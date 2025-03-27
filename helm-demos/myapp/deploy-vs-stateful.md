## Deployment v/s StatefulSet

Context | Deployment | StatefulSet
--------|------------|--------------
Pod Names | deployname-rsname-podname | setname-INDEX (starts with 0)
Pod Names retained after recreate | No | Yes
Pod creation | Parallel Pod creation | Sequential pod creation
PVC | Any pod can claim PVC | Each pod gets a dedicated PVC, after pod is recreated It can auto claim its PVC
