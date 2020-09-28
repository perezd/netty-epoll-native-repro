load("@rules_graal//graal:graal.bzl", "graal_binary")
load("@rules_java//java:defs.bzl", "java_library")

java_library(
    name = "main",
    srcs = ["Main.java"],
    deps = [
        "@maven//:io_netty_netty_codec_http",
        "@maven//:io_netty_netty_transport",
        "@maven//:io_netty_netty_transport_native_epoll_linux_x86_64",
        "@maven//:io_netty_netty_handler",
    ],
)

graal_binary(
    name = "main-native",
    graal_extra_args = [
        "-H:+TraceClassInitialization",
        "--static",
    ],
    main_class = "Main",
    deps = [":main"],
)
