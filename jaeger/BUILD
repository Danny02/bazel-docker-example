load("@io_bazel_rules_docker//container:container.bzl", "container_image")
load("@io_bazel_rules_docker//container:container.bzl", "container_layer")

container_layer(
    name = "jaeger_base",
    tars = ["@jaeger//file"],
)

container_image(
    name = "jaeger_agent",
    base = "@alpine_linux_amd64//image",
    layers = ["jaeger_base"],
    entrypoint = ["/jaeger-1.13.0-linux-amd64/jaeger-agent"],
    ports = [
        "5775/udp",
        "6831/udp",
        "6832/udp",
        "5778"
    ],
)

container_image(
    name = "jaeger_collector",
    base = "@alpine_linux_amd64//image",
    layers = ["jaeger_base"],
    entrypoint = ["/jaeger-1.13.0-linux-amd64/jaeger-collector"],
    ports = ["14267", "14250"]
)

container_image(
    name = "jaeger_query",
    base = "@alpine_linux_amd64//image",
    layers = ["jaeger_base"],
    entrypoint = ["/jaeger-1.13.0-linux-amd64/jaeger-query"],
    ports = ["16686"]
)