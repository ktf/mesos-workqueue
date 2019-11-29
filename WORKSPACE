workspace(name="O2")

load("@bazel_tools//tools/build_defs/repo:git.bzl", "git_repository", "new_git_repository")
load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

all_content = """filegroup(name = "all", srcs = glob(["**"]), visibility = ["//visibility:public"])"""

http_archive(
  name = "rules_foreign_cc",
  strip_prefix = "rules_foreign_cc-master",
  url = "https://github.com/bazelbuild/rules_foreign_cc/archive/master.zip",
  sha256 = "bdfc2734367a1242514251c7ed2dd12f65dd6d19a97e6a2c61106851be8e7fb8"
)

load("@rules_foreign_cc//:workspace_definitions.bzl", "rules_foreign_cc_dependencies")

rules_foreign_cc_dependencies()

http_archive(
  name = "boost",
  build_file_content = all_content,
  strip_prefix = "boost_1_68_0",
  sha256 = "da3411ea45622579d419bfda66f45cd0f8c32a181d84adfa936f5688388995cf",
  urls = ["https://dl.bintray.com/boostorg/release/1.68.0/source/boost_1_68_0.tar.gz"],
)

http_archive(
  name = "mesos",
  build_file_content = all_content,
  strip_prefix = "mesos-1.0.4",
  sha256 = "7c7b1d734d7c54b91586672ccb04aa176aba83eac3864f8bf597689c48358896",
  urls = ["http://archive.apache.org/dist/mesos/1.0.4/mesos-1.0.4.tar.gz"]
)

http_archive(
  name = "apr",
  build_file_content = all_content,
  strip_prefix = "apr-1.7.0",
  sha256 = "48e9dbf45ae3fdc7b491259ffb6ccf7d63049ffacbc1c0977cced095e4c2d5a2",
  urls = ["http://apache.mediamirrors.org//apr/apr-1.7.0.tar.gz"]
)

http_archive(
  name = "apr-util",
  build_file_content = all_content,
  strip_prefix = "apr-util-1.6.1",
  sha256 = "b65e40713da57d004123b6319828be7f1273fbc6490e145874ee1177e112c459",
  urls = ["http://apache.mediamirrors.org//apr/apr-util-1.6.1.tar.gz"]
)

lz4_content = """
licenses(["notice"])

cc_library(
    name = "lz4",
    srcs = [
        "lib/lz4.c",
        "lib/lz4hc.c",
        "lib/lz4frame.c",
        "lib/xxhash.c",
        ],
    hdrs = [
        "lib/lz4.c",
        "lib/lz4.h",
        "lib/lz4hc.h",
        "lib/lz4frame.h",
        "lib/xxhash.h",
        ],
    visibility = ["//visibility:public"]
)
"""

http_archive(
  name = "lz4",
  build_file_content = lz4_content,
  strip_prefix = "lz4-1.9.2",
  sha256 = "658ba6191fa44c92280d4aa2c271b0f4fbc0e34d249578dd05e50e76d0e5efcc",
  urls = ["https://github.com/lz4/lz4/archive/v1.9.2.tar.gz"]
)

utf8proc_content = """
licenses(["notice"])

cc_library(
    name = "utf8proc",
    srcs = [
        "utf8proc.c",
        "utf8proc.h",
        ],
    hdrs = [
        "utf8proc.h",
        "utf8proc_data.c"
        ],
    visibility = ["//visibility:public"]
)
"""


http_archive(
  name = "utf8proc",
  build_file_content = utf8proc_content,
  strip_prefix = "utf8proc-2.4.0",
  sha256 = "b2e5d547c1d94762a6d03a7e05cea46092aab68636460ff8648f1295e2cdfbd7",
  urls = ["https://github.com/JuliaStrings/utf8proc/archive/v2.4.0.tar.gz"]
)

http_archive(
  name = "svn",
  build_file_content = all_content,
  strip_prefix = "subversion-1.10.6",
  sha256 = "2ab75c61a62d96defc954b599585b79f627e4e235094a17da94dc55b564727c1",
  urls = ["http://apache.mirrors.ovh.net/ftp.apache.org/dist/subversion/subversion-1.10.6.tar.gz"]
)
