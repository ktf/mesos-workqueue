load("@rules_foreign_cc//tools/build_defs:cmake.bzl", "cmake_external")
load("@rules_foreign_cc//tools/build_defs:boost_build.bzl", "boost_build")
load("@rules_foreign_cc//tools/build_defs:configure.bzl", "configure_make")

configure_make(
    name = "apr",
    configure_options = [
        "--enable-shared=no",
        "--with-pic",
    ],
    lib_source = "@apr//:all",
    configure_env_vars = {
      "AR": "",
    },
    static_libraries = ["libapr-1.a"],
)

configure_make(
    name = "apr-util",
    configure_options = [
        "--enable-shared=no",
        "--with-pic",
        "--with-apr=$EXT_BUILD_DEPS/apr"
    ],
    lib_source = "@apr-util//:all",
    configure_env_vars = {
      "AR": "",
    },
    static_libraries = ["libaprutil-1.a"],
    deps = ["//:apr"]
)

configure_make(
    name = "svn",
    configure_options = [
        "--enable-shared=no",
        "--with-pic",
        "--with-apr=$EXT_BUILD_DEPS/apr",
        "--with-apr-util=$EXT_BUILD_DEPS/apr-util",
        "--with-lz4=$EXT_BUILD_DEPS",
        "CFLAGS='-Dredacted=\"redacted\"'",
        "CXXFLAGS='-Dredacted=\"redacted\"'",
#        "AR=''"
    ],
    lib_source = "@svn//:all",
    configure_env_vars = {
#      "AR": "",
    },
    static_libraries = ["libsvn_subr-1.a"],
    deps = ["//:apr", "//:apr-util", "@lz4//:lz4", "@utf8proc//:utf8proc"]
)

configure_make(
  name = "mesos",
  lib_source = "@mesos//:all",
  static_libraries = ["libmesos.a"],
  configure_options = [
      "--disable-dependency-tracking",
      "--disable-java",
      "--with-apr=$EXT_BUILD_DEPS/apr",
      "--with-svn=$EXT_BUILD_DEPS/svn"
  ],
  configure_env_vars = {
    "AR": "",
  },
  deps = ["//:apr", "//:svn"]
)

cc_binary(
  name = "mesos-workqueue",
  srcs = ["WorkqueueScheduler.cc", "WorkqueueScheduler.h", "main.cc"]
)
