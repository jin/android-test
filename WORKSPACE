# TODO(b/114418172): rename to androidx_test. Requires a bazel change
workspace(name = "android_test_support")

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

RULES_MAVEN_COMMIT = "0.0.4"

http_archive(
    name = "rules_maven",
    strip_prefix = "rules_maven-%s" % RULES_MAVEN_COMMIT,
    url = "https://github.com/jin/rules_maven/archive/%s.zip" % RULES_MAVEN_COMMIT,
)

load("@rules_maven//:defs.bzl", "maven_install")
load("//build_extensions:axt_versions.bzl", "ANDROIDX_VERSION", "ANDROIDX_LIFECYCLE_VERSION", "GOOGLE_MATERIAL_VERSION", "ANDROIDX_MULTIDEX_VERSION")

maven_install(
    artifacts = [
        "androidx.appcompat:appcompat:" + ANDROIDX_VERSION,
        "com.google.android.material:material:" + GOOGLE_MATERIAL_VERSION,
        "androidx.multidex:multidex:" + ANDROIDX_MULTIDEX_VERSION,
        "androidx.annotation:annotation:" + ANDROIDX_VERSION,
        "androidx.lifecycle:lifecycle-common:" + ANDROIDX_LIFECYCLE_VERSION,
        "androidx.core:core:" + ANDROIDX_VERSION,
        "androidx.legacy:legacy-support-core-ui:" + ANDROIDX_VERSION,
        "androidx.legacy:legacy-support-core-utils:" + ANDROIDX_VERSION,
        "androidx.fragment:fragment:" + ANDROIDX_VERSION,
        "androidx.legacy:legacy-support-v4:" + ANDROIDX_VERSION,
        "androidx.recyclerview:recyclerview:" + ANDROIDX_VERSION,
        "androidx.viewpager:viewpager:" + ANDROIDX_VERSION,
        "androidx.drawerlayout:drawerlayout:" + ANDROIDX_VERSION,
        "androidx.cursoradapter:cursoradapter:" + ANDROIDX_VERSION,
    ],
    repositories = [
        "https://bintray.com/bintray/jcenter",
        "https://maven.google.com",
    ],
)

android_sdk_repository(
    name = "androidsdk",
    api_level = 28,
    build_tools_version = "28.0.3",
)

load("//:repo.bzl", "android_test_repositories")

android_test_repositories(with_dev_repositories = True)

load("@robolectric//bazel:robolectric.bzl", "robolectric_repositories")

robolectric_repositories()

# Kotlin toolchains
rules_kotlin_version = "c5e25d71af96d446af4a8cb283c261537fc9f64e"

http_archive(
    name = "io_bazel_rules_kotlin",
    strip_prefix = "rules_kotlin-%s" % rules_kotlin_version,
    type = "zip",
    urls = ["https://github.com/bazelbuild/rules_kotlin/archive/%s.zip" % rules_kotlin_version],
)

load("@io_bazel_rules_kotlin//kotlin:kotlin.bzl", "kotlin_repositories", "kt_register_toolchains")

kotlin_repositories()

kt_register_toolchains()
