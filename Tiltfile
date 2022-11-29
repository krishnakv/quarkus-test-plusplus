# -*- mode: Python -*-

allow_k8s_contexts('<IF NON-MINIKUBE CONTEXT>')
default_registry('<IF NON-LOCAL REGISTRY>')

docker_build(
  'quarkus-sync-image-tilt',
  context='.',
  dockerfile='./src/main/docker/Dockerfile.mvn',
  live_update=[sync('./src/', '/project/src'),
               sync('./src/pom.xml', '/project/pom.xml') ],
  entrypoint = 'mvn quarkus:dev')

k8s_yaml('src/main/kubernetes/app.yaml')
k8s_resource('quarkus-sync-demo-tilt', port_forwards=[8080,5005])
