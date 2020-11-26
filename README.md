

docker login registry.gitlab.com

bazel build cc-docker/image

bazel run cc-docker/image-push

