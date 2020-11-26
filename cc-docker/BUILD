package(default_visibility = ["//visibility:public"])

name = "cc-docker"

load(
    "@io_bazel_rules_docker//container:container.bzl",
    "container_image",
    "container_push",
)

load("@rules_pkg//:pkg.bzl", "pkg_tar")
 
pkg_tar(
    name = "fruit_tar",
    srcs = glob(
        ["fruits/*"],
    ),
    mode = "0755",
)
 

container_image(
    name = "image",
    base = "@hello_app//image",
    stamp = True,
    tars = [
        ":fruit_tar",
    ],
)
 
#load("//tools:version.bzl", "git_tag_plus_sha")

#git_tag_plus_sha(
#    name = "version",
#    target = ":image",
#)

container_push(
    name = "image-push",
    format = "Docker",
    image = ":image",
    registry = "registry.gitlab.com",
    repository = "marcin.gosk/bazel-image-test",
    tag = "one_one_one"
)