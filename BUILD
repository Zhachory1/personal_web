load("@rules_pkg//:pkg.bzl", "pkg_tar", "pkg_deb")
load("@io_bazel_rules_docker//container:container.bzl", "container_image")

pkg_tar(
    name = "web_server_tar",
    extension = "tar.gz",
    strip_prefix = "/server",
    srcs = [
        "//server",
        "//public",
    ],
    mode = "0755",
)


container_image(
    name = "web_server_image",
    base = "@alpine_linux_amd64//image",
    entrypoint = ["./server_/server"],
    tars = [":web_server_tar"],
    mode = "0755",
)