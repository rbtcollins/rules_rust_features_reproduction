load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

http_archive(
    name = "rules_rust",
    sha256 = "36ab8f9facae745c9c9c1b33d225623d976e78f2cc3f729b7973d8c20934ab95",
    urls = ["https://github.com/bazelbuild/rules_rust/releases/download/0.31.0/rules_rust-v0.31.0.tar.gz"],
)

load("@rules_rust//rust:repositories.bzl", "rules_rust_dependencies", "rust_register_toolchains")

rules_rust_dependencies()

rust_register_toolchains(
    edition = "2021",
    versions = ["1.74.0"],
)

load("@rules_rust//crate_universe:repositories.bzl", "crate_universe_dependencies")

crate_universe_dependencies()

load("@rules_rust//crate_universe:defs.bzl", "crates_repository")

crates_repository(
    name = "crate_index",
    annotations = {
    },
    cargo_lockfile = "//:Cargo.lock",
    lockfile = "//:cargo-bazel-lock.json",
    manifests = [
        "//:Cargo.toml",
    ],
    packages = {
    },
    rust_version = "1.74.0",
)

load(
    "@crate_index//:defs.bzl",
    cargo_aliases_crate_repositories = "crate_repositories",
)

cargo_aliases_crate_repositories()

http_archive(
    name = "rules_proto",
    sha256 = "903af49528dc37ad2adbb744b317da520f133bc1cbbecbdd2a6c546c9ead080b",
    strip_prefix = "rules_proto-6.0.0-rc0",
    url = "https://github.com/bazelbuild/rules_proto/releases/download/6.0.0-rc0/rules_proto-6.0.0-rc0.tar.gz",
)

# load("@rules_proto//proto:repositories.bzl", "rules_proto_dependencies", "rules_proto_toolchains")

# rules_proto_dependencies()
# rules_proto_toolchains()

load("@rules_rust//tools/rust_analyzer:deps.bzl", "rust_analyzer_dependencies")

rust_analyzer_dependencies()
