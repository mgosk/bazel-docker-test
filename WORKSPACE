load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

RULES_DOCKER_TAG = "0.15.0"

RULES_DOCKER_SHA = "1698624e878b0607052ae6131aa216d45ebb63871ec497f26c67455b34119c80"

http_archive(
    name = "io_bazel_rules_docker",
    sha256 = RULES_DOCKER_SHA,
    strip_prefix = "rules_docker-%s" % RULES_DOCKER_TAG,
    url = "https://github.com/bazelbuild/rules_docker/releases/download/v{version}/rules_docker-v{version}.tar.gz".format(version = RULES_DOCKER_TAG),

)

load("@io_bazel_rules_docker//toolchains/docker:toolchain.bzl",
    docker_toolchain_configure="toolchain_configure"
)

load(
    "@io_bazel_rules_docker//repositories:repositories.bzl",
    container_repositories = "repositories",
)
container_repositories()

load("@io_bazel_rules_docker//repositories:deps.bzl", container_deps = "deps")

container_deps()

load(
    "@io_bazel_rules_docker//container:container.bzl",
    "container_pull",
)

container_pull(
    name = "hello_app",
    registry = "gcr.io",
    repository = "google-samples/hello-app",
    tag = "1.0",
)