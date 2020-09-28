workspace(name = "grl")

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

http_archive(
    name = "rules_graal",
    sha256 = "c1445dd6263b17b110da69178c238dc0925bbea1bffc93c46f5af4f8027245cc",
    strip_prefix = "rules_graal-master",
    urls = [
        "https://github.com/andyscott/rules_graal/archive/1b5f6deef8352c4b64541bb0f699fd2af5ae6b0b.zip",
    ],
)

load("@rules_graal//graal:graal_bindist.bzl", "graal_bindist_repository")

graal_bindist_repository(
    name = "graal",
    java_version = "11",
    version = "19.3.1",
)

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

RULES_JVM_EXTERNAL_TAG = "3.3"

RULES_JVM_EXTERNAL_SHA = "d85951a92c0908c80bd8551002d66cb23c3434409c814179c0ff026b53544dab"

http_archive(
    name = "rules_jvm_external",
    sha256 = RULES_JVM_EXTERNAL_SHA,
    strip_prefix = "rules_jvm_external-%s" % RULES_JVM_EXTERNAL_TAG,
    url = "https://github.com/bazelbuild/rules_jvm_external/archive/%s.zip" % RULES_JVM_EXTERNAL_TAG,
)

load("@rules_jvm_external//:defs.bzl", "maven_install")
load("@rules_jvm_external//:specs.bzl", "maven")

NETTY_VERSION = "4.1.52.Final"

maven_install(
    artifacts = [
        maven.artifact(
            group = "io.netty",
            artifact = "netty-codec-http",
            version = NETTY_VERSION,
        ),
        maven.artifact(
            group = "io.netty",
            artifact = "netty-transport",
            version = NETTY_VERSION,
        ),
        maven.artifact(
            group = "io.netty",
            artifact = "netty-handler",
            version = NETTY_VERSION,
        ),
        maven.artifact(
            group = "io.netty",
            artifact = "netty-transport-native-epoll",
            version = NETTY_VERSION,
            classifier = "linux-x86_64",
        ),
    ],
    maven_install_json = "@grl//:maven_install.json",
    repositories = [
        "https://jcenter.bintray.com/",
        "https://maven.google.com",
        "https://repo1.maven.org/maven2",
    ],
)

load("@maven//:defs.bzl", "pinned_maven_install")

pinned_maven_install()
