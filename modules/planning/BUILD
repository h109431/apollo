load("//tools:cpplint.bzl", "cpplint")

package(default_visibility = ["//visibility:public"])

cc_library(
    name = "planning_base",
    srcs = [
        "planning_base.cc",
    ],
    hdrs = [
        "planning_base.h",
    ],
    deps = [
        "//modules/common",
        "//modules/common:apollo_app",
        "//modules/common/adapters:adapter_manager",
        "//modules/common/configs:config_gflags",
        "//modules/common/math:quaternion",
        "//modules/common/proto:pnc_point_proto",
        "//modules/common/vehicle_state:vehicle_state_provider",
        "//modules/map/hdmap:hdmap_util",
        "//modules/perception/proto:perception_proto",
        "//modules/planning/common:planning_common",
        "//modules/planning/common/trajectory:trajectory_stitcher",
        "//modules/planning/planner/em:em_planner",
        "//modules/planning/planner/lattice:lattice_planner",
        "//modules/planning/planner/navi:navi_planner",
        "//modules/planning/planner/rtk:rtk_planner",
        "//modules/planning/proto:planning_proto",
        "//modules/planning/proto:traffic_rule_config_proto",
        "//modules/planning/reference_line:reference_line_provider",
        "//modules/planning/tasks/traffic_decider",
        "//modules/prediction/proto:prediction_proto",
        "@ros//:ros_common",
    ],
)

cc_library(
    name = "std_planning_lib",
    srcs = [
        "std_planning.cc",
    ],
    hdrs = [
        "std_planning.h",
    ],
    deps = [
        ":planning_base",
    ],
)

cc_library(
    name = "navi_planning_lib",
    srcs = [
        "navi_planning.cc",
    ],
    hdrs = [
        "navi_planning.h",
    ],
    deps = [
        ":planning_base",
    ],
)

cc_library(
    name = "planning_lib",
    hdrs = [
        "planning.h",
    ],
    deps = [
        ":navi_planning_lib",
        ":std_planning_lib",
    ],
)

cc_binary(
    name = "planning",
    srcs = [
        "main.cc",
        "planning.h",
    ],
    deps = [
        ":planning_lib",
        "//external:gflags",
    ],
)

filegroup(
    name = "planning_testdata",
    srcs = glob([
        "testdata/**",
    ]),
)

filegroup(
    name = "planning_conf",
    srcs = glob([
        "conf/**",
    ]),
)

cpplint()
