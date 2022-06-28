workspace(name = "tf_serving")

# To update TensorFlow to a new revision.
# 1. Update the 'git_commit' args below to include the new git hash.
# 2. Get the sha256 hash of the archive with a command such as...
#    curl -L https://github.com/tensorflow/tensorflow/archive/<git hash>.tar.gz | sha256sum
#    and update the 'sha256' arg with the result.
# 3. Request the new archive to be mirrored on mirror.bazel.build for more
#    reliable downloads.
load("//tensorflow_serving:repo.bzl", "tensorflow_http_archive")

tensorflow_http_archive(
    name = "org_tensorflow",
    #sha256 = "141b1e720753dd9f9f654041ce6a8f84c0cd190500d8264c2cb79b5c3d2c13ff",
    #git_commit = "1436a3d841587d6461ef6776f7baa94d497571cd",

    #sha256 = "ddc255ced2fce5e48fb46840fb551d7151616b74b95d8c5f4f417c985fb63b5b",
    #git_commit = "c81c9c8202e6dddf507de09d8aab54cc3e3680eb",
    ##sha256 = "7f2c299d345dd1f711076be396e0eaefa79231e2ac1570fb553061f24b3e1ac2", 
    ##git_commit = "e5a34da099cd1e881cfd75155225d59ad49b8bc5",
#    sha256 = "a7b7b0fdf4a596f6ef51a524251c6c88e06b2457b4a2bb3be6f4856bc77f45e6",
#    git_commit = "204dd7a19ec804fc24fbbc9f06e2f10643e647b4",
    sha256 = "b369cbbb7b36aebe7d4c3b0982c3074f077fdb21e6a9a04911c78be987c97388",
		git_commit = "4bb3df536aeb7ccfade068360801d156cc2913fe",
)

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

# START: Upstream TensorFlow dependencies
# TensorFlow build depends on these dependencies.
# Needs to be in-sync with TensorFlow sources.
http_archive(
    name = "io_bazel_rules_closure",
    sha256 = "ddce3b3a3909f99b28b25071c40b7fec7e2e1d1d1a4b2e933f3082aa99517105",
    strip_prefix = "rules_closure-316e6133888bfc39fb860a4f1a31cfcbae485aef",
    urls = [
        "https://mirror.bazel.build/github.com/bazelbuild/rules_closure/archive/316e6133888bfc39fb860a4f1a31cfcbae485aef.tar.gz",
        "https://github.com/bazelbuild/rules_closure/archive/316e6133888bfc39fb860a4f1a31cfcbae485aef.tar.gz",  # 2019-03-21
    ],
)
http_archive(
    name = "bazel_skylib",
    sha256 = "2c62d8cd4ab1e65c08647eb4afe38f51591f43f7f0885e7769832fa137633dcb",
    strip_prefix = "bazel-skylib-0.7.0",
    urls = ["https://github.com/bazelbuild/bazel-skylib/archive/0.7.0.tar.gz"],
)
# END: Upstream TensorFlow dependencies

# Please add all new TensorFlow Serving dependencies in workspace.bzl.
load("//tensorflow_serving:workspace.bzl", "tf_serving_workspace")

tf_serving_workspace()

# Specify the minimum required bazel version.
load("@org_tensorflow//tensorflow:version_check.bzl", "check_bazel_version_at_least")

check_bazel_version_at_least("0.24.1")
