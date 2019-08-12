load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

# Download the rules_docker repository at release v0.9.0
http_archive(
    name = "io_bazel_rules_docker",
    sha256 = "e513c0ac6534810eb7a14bf025a0f159726753f97f74ab7863c650d26e01d677",
    strip_prefix = "rules_docker-0.9.0",
    urls = ["https://github.com/bazelbuild/rules_docker/archive/v0.9.0.tar.gz"],
)

load(
    "@io_bazel_rules_docker//repositories:repositories.bzl",
    container_repositories = "repositories",
)
container_repositories()

# This is NOT needed when going through the language lang_image
# "repositories" function(s).
load("@io_bazel_rules_docker//repositories:deps.bzl", container_deps = "deps")

container_deps()

load(
    "@io_bazel_rules_docker//container:container.bzl",
    "container_pull",
)

container_pull(
    name = "alpine_linux_amd64",
    registry = "index.docker.io",
    repository = "library/alpine",
    tag = "3.10.1",
)

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_file")
http_file(
    name = "jaeger",
    downloaded_file_path = "jaeger.tar.gz",
    urls = ["https://github.com/jaegertracing/jaeger/releases/download/v1.13.0/jaeger-1.13.0-linux-amd64.tar.gz"],
    sha256 = "2d65c2096dd0c5424c546aa18c3aacbeaa74f9dee86e348af7446394a69f7c7e",
)
