load("@io_bazel_rules_docker//container:container.bzl", "container_image", "container_layer", "container_bundle")

container_image(
    name = "agent",
    base = "@alpine_linux_amd64//image",
    files = ["@jaeger_bin//:jaeger-agent"],
    entrypoint = ["/jaeger-1.13.0-linux-amd64/jaeger-agent"],
    ports = [
        "5775/udp",
        "6831/udp",
        "6832/udp",
        "5778"
    ],
)

container_image(
    name = "collector",
    base = "@alpine_linux_amd64//image",
    files = ["@jaeger_bin//:jaeger-collector"],
    entrypoint = ["/jaeger-1.13.0-linux-amd64/jaeger-collector"],
    ports = ["14267", "14250"]
)

container_image(
    name = "query",
    base = "@alpine_linux_amd64//image",
    files = ["@jaeger_bin//:jaeger-query"],
    entrypoint = ["/jaeger-1.13.0-linux-amd64/jaeger-query"],
    ports = ["16686"]
)

container_bundle(
    name = "bundle_all",
    images = {
        "jaeger/agent:1.13.0": ":agent",
        "jaeger/collector:1.13.0": ":collector",
        "jaeger/query:1.13.0": ":query",
    },
)