load("@io_bazel_rules_docker//container:container.bzl", "container_image")

package(
    default_visibility = ["//src:__subpackages__"],
)

filegroup(
    name = "configs",
    srcs = glob(["logging.properties"]),
    visibility = ["//visibility:public"],
)

java_library(
    name = "common",
    srcs = glob([
        "common/*.java",
        "common/function/*.java",
        "common/io/*.java",
        "common/redis/*.java",
    ]),
    deps = [
        "@maven//:com_github_jnr_jnr_constants",
        "@maven//:com_github_jnr_jnr_ffi",
        "@maven//:com_github_jnr_jnr_posix",
        "@maven//:com_google_code_findbugs_jsr305",
        "@maven//:com_google_guava_guava",
        "@maven//:com_google_guava_failureaccess",
        "@maven//:com_google_protobuf_protobuf_java",
        "@maven//:com_google_protobuf_protobuf_java_util",
        "@maven//:io_grpc_grpc_api",
        "@maven//:io_grpc_grpc_context",
        "@maven//:io_grpc_grpc_protobuf",
        "@maven//:org_threeten_threetenbp",
        "//src/main/protobuf:build_buildfarm_v1test_buildfarm_java_proto",
        "@googleapis//:google_longrunning_operations_java_proto",
        "@googleapis//:google_rpc_code_java_proto",
        "@googleapis//:google_rpc_error_details_java_proto",
        "@remote_apis//:build_bazel_remote_execution_v2_remote_execution_java_proto",
        "//third_party/jedis",
    ],
)

java_library(
    name = "common-cache",
    srcs = glob(["common/cache/*.java"]),
    deps = [
        "@maven//:com_google_code_findbugs_jsr305",
        "@maven//:com_google_errorprone_error_prone_annotations",
        "@maven//:com_google_guava_guava",
        "@maven//:com_google_guava_failureaccess",
        "@maven//:com_google_j2objc_j2objc_annotations",
        "@maven//:org_checkerframework_checker_qual",
    ],
)

java_library(
    name = "common-grpc",
    srcs = glob([
        "common/grpc/*.java",
    ]),
    deps = [
        ":common",
        "@maven//:com_google_code_findbugs_jsr305",
        "@maven//:com_google_guava_guava",
        "@maven//:com_google_protobuf_protobuf_java",
        "@maven//:io_grpc_grpc_api",
        "@maven//:io_grpc_grpc_context",
        "@maven//:io_grpc_grpc_core",
        "@maven//:io_grpc_grpc_protobuf",
        "@maven//:io_grpc_grpc_stub",
        "@googleapis//:google_bytestream_bytestream_java_grpc",
        "@googleapis//:google_bytestream_bytestream_java_proto",
        "@remote_apis//:build_bazel_remote_execution_v2_remote_execution_java_proto",
    ],
)

java_library(
    name = "common-redis",
    srcs = glob([
        "common/redis/*.java",
    ]),
    deps = [
        ":common",
        "//src/main/protobuf:build_buildfarm_v1test_buildfarm_java_proto",
        "//third_party/jedis",
        "@maven//:com_google_guava_guava",
        "@maven//:io_grpc_grpc_api",
    ],
)

java_library(
    name = "instance",
    srcs = [
        "instance/ExcessiveWriteSizeException.java",
        "instance/Instance.java",
        "instance/Utils.java",
    ],
    deps = [
        ":common",
        "@maven//:com_google_code_findbugs_jsr305",
        "@maven//:com_google_guava_guava",
        "@maven//:com_google_guava_failureaccess",
        "@maven//:com_google_protobuf_protobuf_java",
        "@maven//:io_grpc_grpc_api",
        "@maven//:io_grpc_grpc_core",
        "@maven//:io_grpc_grpc_protobuf",
        "@maven//:io_grpc_grpc_stub",
        "//src/main/protobuf:build_buildfarm_v1test_buildfarm_java_proto",
        "@googleapis//:google_longrunning_operations_java_proto",
        "@remote_apis//:build_bazel_remote_execution_v2_remote_execution_java_proto",
    ],
)

java_library(
    name = "server-instance",
    srcs = [
        "instance/AbstractServerInstance.java",
        "instance/GetDirectoryFunction.java",
        "instance/OperationsMap.java",
        "instance/WatchFuture.java",
    ],
    deps = [
        ":ac",
        ":cas",
        ":common",
        ":instance",
        "@maven//:com_google_code_findbugs_jsr305",
        "@maven//:com_google_guava_guava",
        "@maven//:com_google_protobuf_protobuf_java",
        "@maven//:io_grpc_grpc_api",
        "@maven//:io_grpc_grpc_context",
        "@maven//:io_grpc_grpc_core",
        "@maven//:io_grpc_grpc_netty",
        "@maven//:io_grpc_grpc_protobuf",
        "@maven//:io_grpc_grpc_stub",
        "//src/main/protobuf:build_buildfarm_v1test_buildfarm_java_proto",
        "@googleapis//:google_longrunning_operations_java_proto",
        "@googleapis//:google_rpc_code_java_proto",
        "@googleapis//:google_rpc_error_details_java_proto",
        "@googleapis//:google_rpc_status_java_proto",
        "@remote_apis//:build_bazel_remote_execution_v2_remote_execution_java_proto",
    ],
)

java_library(
    name = "memory-instance",
    srcs = glob(["instance/memory/*.java"]),
    deps = [
        ":ac",
        ":cas",
        ":common",
        ":instance",
        ":server-instance",
        ":worker-queues",
        "@maven//:com_google_code_findbugs_jsr305",
        "@maven//:com_google_guava_guava",
        "@maven//:com_google_protobuf_protobuf_java",
        "@maven//:com_google_protobuf_protobuf_java_util",
        "@maven//:io_grpc_grpc_api",
        "@maven//:io_grpc_grpc_context",
        "@maven//:io_grpc_grpc_core",
        "@maven//:io_grpc_grpc_netty",
        "@maven//:io_grpc_grpc_protobuf",
        "@maven//:io_grpc_grpc_stub",
        "//src/main/protobuf:build_buildfarm_v1test_buildfarm_java_proto",
        "@googleapis//:google_longrunning_operations_java_proto",
        "@googleapis//:google_rpc_code_java_proto",
        "@googleapis//:google_rpc_error_details_java_proto",
        "@googleapis//:google_rpc_status_java_proto",
        "@remote_apis//:build_bazel_remote_execution_v2_remote_execution_java_proto",
    ],
)

java_library(
    name = "shard-instance",
    srcs = glob(["instance/shard/*.java"]),
    deps = [
        ":common",
        ":common-cache",
        ":common-grpc",
        ":common-redis",
        ":instance",
        ":server-instance",
        ":stub-instance",
        ":worker-queues",
        "@maven//:com_google_code_findbugs_jsr305",
        "@maven//:com_google_guava_guava",
        "@maven//:com_google_protobuf_protobuf_java",
        "@maven//:com_google_protobuf_protobuf_java_util",
        "@maven//:io_grpc_grpc_api",
        "@maven//:io_grpc_grpc_context",
        "@maven//:io_grpc_grpc_core",
        "@maven//:io_grpc_grpc_netty",
        "@maven//:io_grpc_grpc_protobuf",
        "@maven//:io_grpc_grpc_stub",
        "@maven//:io_netty_netty_codec_http",
        "@maven//:org_apache_commons_commons_pool2",
        "//src/main/protobuf:build_buildfarm_v1test_buildfarm_java_proto",
        "//third_party/jedis",
        "@googleapis//:google_rpc_code_java_proto",
        "@googleapis//:google_rpc_error_details_java_proto",
        "@remote_apis//:build_bazel_remote_execution_v2_remote_execution_java_grpc",
        "@remote_apis//:build_bazel_remote_execution_v2_remote_execution_java_proto",
    ],
)

java_library(
    name = "worker-queues",
    srcs = glob(["instance/memory/queues/*.java"]),
    deps = [
        ":ac",
        ":cas",
        ":common",
        ":instance",
        ":server-instance",
        "@maven//:com_google_code_findbugs_jsr305",
        "@maven//:com_google_guava_guava",
        "@maven//:com_google_protobuf_protobuf_java",
        "@maven//:com_google_protobuf_protobuf_java_util",
        "@maven//:io_grpc_grpc_api",
        "@maven//:io_grpc_grpc_context",
        "@maven//:io_grpc_grpc_core",
        "@maven//:io_grpc_grpc_netty",
        "@maven//:io_grpc_grpc_protobuf",
        "@maven//:io_grpc_grpc_stub",
        "//src/main/protobuf:build_buildfarm_v1test_buildfarm_java_proto",
        "@googleapis//:google_longrunning_operations_java_proto",
        "@googleapis//:google_rpc_code_java_proto",
        "@googleapis//:google_rpc_error_details_java_proto",
        "@googleapis//:google_rpc_status_java_proto",
        "@remote_apis//:build_bazel_remote_execution_v2_remote_execution_java_proto",
    ],
)

java_library(
    name = "server",
    srcs = glob(["server/**/*.java"]),
    visibility = ["//visibility:public"],
    deps = [
        ":cas",
        ":common",
        ":common-grpc",
        ":instance",
        ":memory-instance",
        ":shard-instance",
        "@maven//:com_github_pcj_google_options",
        "@maven//:com_google_code_findbugs_jsr305",
        "@maven//:com_google_guava_guava",
        "@maven//:com_google_protobuf_protobuf_java",
        "@maven//:io_grpc_grpc_api",
        "@maven//:io_grpc_grpc_context",
        "@maven//:io_grpc_grpc_core",
        "@maven//:io_grpc_grpc_netty",
        "@maven//:io_grpc_grpc_protobuf",
        "@maven//:io_grpc_grpc_services",
        "@maven//:io_grpc_grpc_stub",
        "@maven//:org_threeten_threetenbp",
        "//src/main/protobuf:build_buildfarm_v1test_buildfarm_java_grpc",
        "//src/main/protobuf:build_buildfarm_v1test_buildfarm_java_proto",
        "@googleapis//:google_bytestream_bytestream_java_grpc",
        "@googleapis//:google_bytestream_bytestream_java_proto",
        "@googleapis//:google_longrunning_operations_java_grpc",
        "@googleapis//:google_rpc_code_java_proto",
        "@remote_apis//:build_bazel_remote_execution_v2_remote_execution_java_grpc",
        "@remote_apis//:build_bazel_remote_execution_v2_remote_execution_java_proto",
        "@remote_apis//:build_bazel_semver_java_proto",
    ],
)

java_binary(
    name = "buildfarm-server",
    classpath_resources = [
        ":configs",
    ],
    main_class = "build.buildfarm.server.BuildFarmServer",
    visibility = ["//visibility:public"],
    runtime_deps = [
        ":server",
    ],
)

container_image(
    name = "server.container",
    base = "@java_base//image",
    cmd = [
        "buildfarm-server_deploy.jar",
        "/config/server.config",
        "--port",
        "8980",
    ],
    # leverage the implicit target of the buildfarm-server to get a fat jar.
    # this is simply a workaround for the fact that we have so many dependencies,
    # so we'd want some wrappy script. This seemed more straightforward.
    # https://docs.bazel.build/versions/master/be/java.html#java_binary_implicit_outputs
    files = [
        ":buildfarm-server_deploy.jar",
    ],
    visibility = ["//visibility:public"],
)

java_library(
    name = "stub-instance",
    srcs = glob(["instance/stub/*.java"]),
    deps = [
        ":common",
        ":common-grpc",
        ":instance",
        "@maven//:com_google_code_findbugs_jsr305",
        "@maven//:com_google_guava_guava",
        "@maven//:com_google_protobuf_protobuf_java",
        "@maven//:io_grpc_grpc_api",
        "@maven//:io_grpc_grpc_context",
        "@maven//:io_grpc_grpc_core",
        "@maven//:io_grpc_grpc_netty",
        "@maven//:io_grpc_grpc_protobuf",
        "@maven//:io_grpc_grpc_stub",
        "//src/main/protobuf:build_buildfarm_v1test_buildfarm_java_grpc",
        "//src/main/protobuf:build_buildfarm_v1test_buildfarm_java_proto",
        "@googleapis//:google_bytestream_bytestream_java_grpc",
        "@googleapis//:google_bytestream_bytestream_java_proto",
        "@googleapis//:google_longrunning_operations_java_grpc",
        "@googleapis//:google_longrunning_operations_java_proto",
        "@googleapis//:google_rpc_code_java_proto",
        "@remote_apis//:build_bazel_remote_execution_v2_remote_execution_java_grpc",
        "@remote_apis//:build_bazel_remote_execution_v2_remote_execution_java_proto",
    ],
)

java_library(
    name = "shard-worker",
    srcs = glob(["worker/shard/*.java"]),
    visibility = ["//visibility:public"],
    deps = [
        ":cas",
        ":common",
        ":common-grpc",
        ":instance",
        ":memory-instance",
        ":server",
        ":server-instance",
        ":shard-instance",
        ":stub-instance",
        ":worker",
        ":worker-cgroup",
        "@maven//:com_github_pcj_google_options",
        "@maven//:com_google_guava_guava",
        "@maven//:com_google_protobuf_protobuf_java",
        "@maven//:com_google_protobuf_protobuf_java_util",
        "@maven//:io_grpc_grpc_api",
        "@maven//:io_grpc_grpc_context",
        "@maven//:io_grpc_grpc_core",
        "@maven//:io_grpc_grpc_netty",
        "@maven//:io_grpc_grpc_protobuf",
        "@maven//:io_grpc_grpc_stub",
        "//src/main/protobuf:build_buildfarm_v1test_buildfarm_java_proto",
        "@googleapis//:google_rpc_error_details_java_proto",
    ],
)

java_binary(
    name = "buildfarm-shard-worker",
    classpath_resources = [
        ":configs",
    ],
    main_class = "build.buildfarm.worker.shard.Worker",
    runtime_deps = [
        ":shard-worker",
    ],
)

container_image(
    name = "buildfarm-shard-worker.container",
    base = "@java_base//image",
    # leverage the implicit target of the buildfarm-shard-worker to get a fat jar.
    # this is simply a workaround for the fact that we have so many dependencies,
    # so we'd want some wrappy script. This seemed more straightforward.
    # https://docs.bazel.build/versions/master/be/java.html#java_binary_implicit_outputs
    files = [
        ":buildfarm-shard-worker_deploy.jar",
    ],
    visibility = ["//visibility:public"],
)

java_library(
    name = "worker-cgroup",
    srcs = glob(["worker/cgroup/*.java"]),
    deps = [
        ":worker",
        "@maven//:com_google_code_findbugs_jsr305",
    ],
)

java_library(
    name = "worker",
    srcs = glob(["worker/*.java"]),
    deps = [
        ":cas",
        ":common",
        ":instance",
        ":stub-instance",
        "@maven//:com_github_jnr_jffi_native",
        "@maven//:com_github_jnr_jnr_constants",
        "@maven//:com_github_jnr_jnr_ffi",
        "@maven//:com_github_jnr_jnr_posix",
        "@maven//:com_github_pcj_google_options",
        "@maven//:com_github_serceman_jnr_fuse",
        "@maven//:com_google_code_findbugs_jsr305",
        "@maven//:com_google_guava_guava",
        "@maven//:com_google_protobuf_protobuf_java",
        "@maven//:com_google_protobuf_protobuf_java_util",
        "@maven//:io_grpc_grpc_api",
        "@maven//:io_grpc_grpc_context",
        "@maven//:io_grpc_grpc_core",
        "@maven//:io_grpc_grpc_netty",
        "@maven//:io_grpc_grpc_protobuf",
        "@maven//:io_grpc_grpc_stub",
        "//src/main/protobuf:build_buildfarm_v1test_buildfarm_java_proto",
        "@googleapis//:google_rpc_code_java_proto",
        "@googleapis//:google_rpc_error_details_java_proto",
    ],
)

java_library(
    name = "operationqueue-worker",
    srcs = glob(["worker/operationqueue/*.java"]),
    deps = [
        ":common",
        ":common-grpc",
        ":instance",
        ":stub-instance",
        ":worker",
        "@maven//:com_github_pcj_google_options",
        "@maven//:com_google_code_findbugs_jsr305",
        "@maven//:com_google_guava_guava",
        "@maven//:com_google_protobuf_protobuf_java",
        "@maven//:io_grpc_grpc_api",
        "@maven//:io_grpc_grpc_context",
        "@maven//:io_grpc_grpc_core",
        "@maven//:io_grpc_grpc_netty",
        "@maven//:io_grpc_grpc_protobuf",
        "@maven//:io_grpc_grpc_stub",
        "//src/main/protobuf:build_buildfarm_v1test_buildfarm_java_proto",
    ],
)

java_library(
    name = "cas",
    srcs = glob(["cas/*.java"]),
    deps = [
        ":common",
        ":common-grpc",
        ":stub-instance",
        "@maven//:com_google_code_findbugs_jsr305",
        "@maven//:com_google_guava_guava",
        "@maven//:com_google_protobuf_protobuf_java",
        "@maven//:io_grpc_grpc_api",
        "@maven//:io_grpc_grpc_core",
        "@maven//:io_grpc_grpc_netty",
        "@maven//:io_grpc_grpc_protobuf",
        "//src/main/protobuf:build_buildfarm_v1test_buildfarm_java_proto",
        "@googleapis//:google_bytestream_bytestream_java_grpc",
        "@googleapis//:google_bytestream_bytestream_java_proto",
        "@googleapis//:google_rpc_code_java_proto",
        "@remote_apis//:build_bazel_remote_execution_v2_remote_execution_java_grpc",
        "@remote_apis//:build_bazel_remote_execution_v2_remote_execution_java_proto",
    ],
)

java_library(
    name = "ac",
    srcs = glob(["ac/*.java"]),
    deps = [
        ":common",
        "@maven//:com_google_guava_guava",
        "@maven//:io_grpc_grpc_api",
        "@maven//:io_grpc_grpc_core",
        "@remote_apis//:build_bazel_remote_execution_v2_remote_execution_java_grpc",
        "@remote_apis//:build_bazel_remote_execution_v2_remote_execution_java_proto",
    ],
)

java_binary(
    name = "buildfarm-operationqueue-worker",
    main_class = "build.buildfarm.worker.operationqueue.Worker",
    visibility = ["//visibility:public"],
    runtime_deps = [
        ":operationqueue-worker",
    ],
)

container_image(
    name = "buildfarm-operationqueue-worker.container",
    base = "@java_base//image",
    cmd = [
        "buildfarm-operationqueue-worker_deploy.jar",
        "/config/worker.config",
    ],
    # leverage the implicit target of the buildfarm-server to get a fat jar.
    # this is simply a workaround for the fact that we have so many dependencies,
    # so we'd want some wrappy script. This seemed more straightforward.
    # https://docs.bazel.build/versions/master/be/java.html#java_binary_implicit_outputs
    files = [
        ":buildfarm-operationqueue-worker_deploy.jar",
    ],
    visibility = ["//visibility:public"],
)

java_binary(
    name = "bf-mount",
    srcs = ["Mount.java"],
    main_class = "build.buildfarm.Mount",
    deps = [
        ":common",
        ":instance",
        ":stub-instance",
        ":worker",
        "@maven//:com_google_guava_guava",
        "@maven//:com_google_protobuf_protobuf_java",
        "@maven//:io_grpc_grpc_api",
        "@maven//:io_grpc_grpc_context",
        "@maven//:io_grpc_grpc_core",
        "@maven//:io_grpc_grpc_netty",
        "@maven//:io_grpc_grpc_protobuf",
        "@maven//:io_grpc_grpc_stub",
        "//src/main/protobuf:build_buildfarm_v1test_buildfarm_java_proto",
        "@googleapis//:google_rpc_code_java_proto",
    ],
)

java_binary(
    name = "bf-cas",
    srcs = ["CASTest.java"],
    classpath_resources = [
        ":configs",
    ],
    main_class = "build.buildfarm.CASTest",
    deps = [
        ":common",
        ":worker",
        "@maven//:com_github_jnr_jnr_constants",
        "@maven//:com_github_jnr_jnr_ffi",
        "@maven//:com_github_jnr_jnr_posix",
        "@maven//:com_google_guava_guava",
        "@remote_apis//:build_bazel_remote_execution_v2_remote_execution_java_proto",
    ],
)

java_plugin(
    name = "io-benchmark-plugins",
    processor_class = "org.openjdk.jmh.generators.BenchmarkProcessor",
    deps = [
        "@maven//:org_openjdk_jmh_jmh_core",
        "@maven//:org_openjdk_jmh_jmh_generator_annprocess",
    ],
)

java_binary(
    name = "io-benchmark",
    srcs = ["IOBenchmark.java"],
    main_class = "build.buildfarm.IOBenchmark",
    plugins = [":io-benchmark-plugins"],
    deps = [
        ":common",
        "@maven//:com_github_jnr_jnr_constants",
        "@maven//:com_github_jnr_jnr_ffi",
        "@maven//:com_github_jnr_jnr_posix",
        "@maven//:org_openjdk_jmh_jmh_core",
    ],
)

java_binary(
    name = "bf-executor",
    srcs = ["Executor.java"],
    main_class = "build.buildfarm.Executor",
    deps = [
        ":common",
        ":stub-instance",
        ":worker",
        "@maven//:com_google_guava_guava",
        "@maven//:com_google_protobuf_protobuf_java",
        "@maven//:io_grpc_grpc_api",
        "@maven//:io_grpc_grpc_context",
        "@maven//:io_grpc_grpc_core",
        "@maven//:io_grpc_grpc_netty",
        "@maven//:io_grpc_grpc_protobuf",
        "@maven//:io_grpc_grpc_stub",
        "@googleapis//:google_bytestream_bytestream_java_grpc",
        "@googleapis//:google_bytestream_bytestream_java_proto",
        "@googleapis//:google_rpc_code_java_proto",
        "@googleapis//:google_rpc_status_java_proto",
        "@remote_apis//:build_bazel_remote_execution_v2_remote_execution_java_grpc",
        "@remote_apis//:build_bazel_remote_execution_v2_remote_execution_java_proto",
    ],
)

java_binary(
    name = "bf-extractor",
    srcs = ["Extract.java"],
    main_class = "build.buildfarm.Extract",
    deps = [
        ":common",
        ":common-grpc",
        "@maven//:com_google_guava_guava",
        "@maven//:com_google_protobuf_protobuf_java",
        "@maven//:io_grpc_grpc_api",
        "@maven//:io_grpc_grpc_context",
        "@maven//:io_grpc_grpc_core",
        "@maven//:io_grpc_grpc_netty",
        "@maven//:io_grpc_grpc_protobuf",
        "@maven//:io_grpc_grpc_stub",
        "@googleapis//:google_bytestream_bytestream_java_grpc",
        "@googleapis//:google_bytestream_bytestream_java_proto",
        "@remote_apis//:build_bazel_remote_execution_v2_remote_execution_java_proto",
    ],
)

java_binary(
    name = "bf-cat",
    srcs = ["Cat.java"],
    classpath_resources = [
        ":configs",
    ],
    main_class = "build.buildfarm.Cat",
    deps = [
        ":common",
        ":instance",
        ":stub-instance",
        "@maven//:com_google_guava_guava",
        "@maven//:com_google_protobuf_protobuf_java",
        "@maven//:com_google_protobuf_protobuf_java_util",
        "@maven//:io_grpc_grpc_api",
        "@maven//:io_grpc_grpc_context",
        "@maven//:io_grpc_grpc_core",
        "@maven//:io_grpc_grpc_netty",
        "@maven//:io_grpc_grpc_protobuf",
        "@maven//:io_grpc_grpc_stub",
        "//src/main/protobuf:build_buildfarm_v1test_buildfarm_java_proto",
        "@googleapis//:google_rpc_code_java_proto",
        "@googleapis//:google_rpc_error_details_java_proto",
    ],
)

java_binary(
    name = "bf-hist",
    srcs = ["Hist.java"],
    main_class = "build.buildfarm.Hist",
    deps = [
        ":common",
        ":instance",
        ":stub-instance",
        "@maven//:com_google_guava_guava",
        "@maven//:com_google_protobuf_protobuf_java",
        "@maven//:io_grpc_grpc_api",
        "@maven//:io_grpc_grpc_context",
        "@maven//:io_grpc_grpc_core",
        "@maven//:io_grpc_grpc_netty",
        "@maven//:io_grpc_grpc_protobuf",
        "@maven//:io_grpc_grpc_stub",
        "@googleapis//:google_longrunning_operations_java_proto",
        "@googleapis//:google_rpc_code_java_proto",
        "@remote_apis//:build_bazel_remote_execution_v2_remote_execution_java_proto",
    ],
)

java_binary(
    name = "buildfarm-http-proxy",
    main_class = "build.buildfarm.proxy.http.HttpProxy",
    runtime_deps = [":http-proxy"],
)

java_library(
    name = "http-proxy",
    srcs = glob(["proxy/http/*.java"]),
    deps = [
        ":common",
        "@maven//:com_github_pcj_google_options",
        "@maven//:com_google_auth_google_auth_library_credentials",
        "@maven//:com_google_auth_google_auth_library_oauth2_http",
        "@maven//:com_google_code_findbugs_jsr305",
        "@maven//:com_google_guava_guava",
        "@maven//:com_google_protobuf_protobuf_java",
        "@maven//:io_grpc_grpc_api",
        "@maven//:io_grpc_grpc_auth",
        "@maven//:io_grpc_grpc_core",
        "@maven//:io_grpc_grpc_netty",
        "@maven//:io_grpc_grpc_protobuf",
        "@maven//:io_grpc_grpc_stub",
        "@maven//:io_netty_netty_buffer",
        "@maven//:io_netty_netty_codec",
        "@maven//:io_netty_netty_codec_http",
        "@maven//:io_netty_netty_common",
        "@maven//:io_netty_netty_handler",
        "@maven//:io_netty_netty_transport",
        "@maven//:io_netty_netty_transport_native_epoll",
        "@maven//:io_netty_netty_transport_native_kqueue",
        "@maven//:io_netty_netty_transport_native_unix_common",
        "//src/main/protobuf:build_buildfarm_v1test_buildfarm_java_proto",
        "@googleapis//:google_bytestream_bytestream_java_grpc",
        "@googleapis//:google_bytestream_bytestream_java_proto",
        "@googleapis//:google_rpc_code_java_proto",
        "@googleapis//:google_rpc_status_java_proto",
        "@remote_apis//:build_bazel_remote_execution_v2_remote_execution_java_grpc",
        "@remote_apis//:build_bazel_remote_execution_v2_remote_execution_java_proto",
    ],
)

java_binary(
    name = "bf-cancel",
    srcs = ["Cancel.java"],
    main_class = "build.buildfarm.Cancel",
    deps = [
        ":common",
        ":instance",
        ":stub-instance",
        "@maven//:io_grpc_grpc_api",
        "@maven//:io_grpc_grpc_context",
        "@maven//:io_grpc_grpc_core",
        "@maven//:io_grpc_grpc_netty",
        "@maven//:io_grpc_grpc_protobuf",
        "@maven//:io_grpc_grpc_stub",
    ],
)
