set(SUBSYS_NAME tests_features)
set(SUBSYS_DESC "Point cloud library features module unit tests")
PCL_SET_TEST_DEPENDENCIES(SUBSYS_DEPS features)
set(OPT_DEPS io keypoints) # module does not depend on these

set(DEFAULT ON)
set(build TRUE)
PCL_SUBSYS_OPTION(build "${SUBSYS_NAME}" "${SUBSYS_DESC}" ${DEFAULT} "${REASON}")
PCL_SUBSYS_DEPEND(build "${SUBSYS_NAME}" DEPS ${SUBSYS_DEPS} OPT_DEPS ${OPT_DEPS})

if (build)
  PCL_ADD_TEST(features_ptr test_features_ptr
               FILES test_ptr.cpp
               LINK_WITH pcl_gtest pcl_features)
  PCL_ADD_TEST(feature_gradient_estimation test_gradient_estimation
               FILES test_gradient_estimation.cpp
               LINK_WITH pcl_gtest pcl_features)
  PCL_ADD_TEST(feature_rift_estimation test_rift_estimation
               FILES test_rift_estimation.cpp
               LINK_WITH pcl_gtest pcl_features)

  if (BUILD_io)
    PCL_ADD_TEST(feature_base test_base_feature
                 FILES test_base_feature.cpp
                 LINK_WITH pcl_gtest pcl_features pcl_io
                 ARGUMENTS "${PCL_SOURCE_DIR}/test/bun0.pcd")
    PCL_ADD_TEST(feature_cppf_estimation test_cppf_estimation
                 FILES test_cppf_estimation.cpp
                 LINK_WITH pcl_gtest pcl_features pcl_io
                 ARGUMENTS "${PCL_SOURCE_DIR}/test/colored_cloud.pcd")
    PCL_ADD_TEST(feature_normal_estimation test_normal_estimation
                 FILES test_normal_estimation.cpp
                 LINK_WITH pcl_gtest pcl_features pcl_io
                 ARGUMENTS "${PCL_SOURCE_DIR}/test/bun0.pcd")
    PCL_ADD_TEST(feature_pfh_estimation test_pfh_estimation
                 FILES test_pfh_estimation.cpp
                 LINK_WITH pcl_gtest pcl_features pcl_io
                 ARGUMENTS "${PCL_SOURCE_DIR}/test/bun0.pcd")

    PCL_ADD_TEST(feature_cvfh_estimation test_cvfh_estimation
                 FILES test_cvfh_estimation.cpp
                 LINK_WITH pcl_gtest pcl_features pcl_io pcl_filters
                 ARGUMENTS "${PCL_SOURCE_DIR}/test/bun0.pcd" "${PCL_SOURCE_DIR}/test/milk.pcd")

    PCL_ADD_TEST(feature_ppf_estimation test_ppf_estimation
                 FILES test_ppf_estimation.cpp
                 LINK_WITH pcl_gtest pcl_features pcl_io
                 ARGUMENTS "${PCL_SOURCE_DIR}/test/bun0.pcd")
    PCL_ADD_TEST(feature_shot_estimation test_shot_estimation
                 FILES test_shot_estimation.cpp
                 LINK_WITH pcl_gtest pcl_features pcl_io
                 ARGUMENTS "${PCL_SOURCE_DIR}/test/bun0.pcd")
    PCL_ADD_TEST(feature_boundary_estimation test_boundary_estimation
                 FILES test_boundary_estimation.cpp
                 LINK_WITH pcl_gtest pcl_features pcl_io
                 ARGUMENTS "${PCL_SOURCE_DIR}/test/bun0.pcd")
    PCL_ADD_TEST(feature_curvatures_estimation test_curvatures_estimation
                 FILES test_curvatures_estimation.cpp
                 LINK_WITH pcl_gtest pcl_features pcl_io
                 ARGUMENTS "${PCL_SOURCE_DIR}/test/bun0.pcd")
    PCL_ADD_TEST(feature_spin_estimation test_spin_estimation
                 FILES test_spin_estimation.cpp
                 LINK_WITH pcl_gtest pcl_features pcl_io
                 ARGUMENTS "${PCL_SOURCE_DIR}/test/bun0.pcd")
    PCL_ADD_TEST(feature_rsd_estimation test_rsd_estimation
                 FILES test_rsd_estimation.cpp
                 LINK_WITH pcl_gtest pcl_features pcl_io pcl_kdtree
                 ARGUMENTS "${PCL_SOURCE_DIR}/test/bun0.pcd")
    PCL_ADD_TEST(feature_grsd_estimation test_grsd_estimation
                 FILES test_grsd_estimation.cpp
                 LINK_WITH pcl_gtest pcl_features pcl_io pcl_kdtree
                 ARGUMENTS "${PCL_SOURCE_DIR}/test/bun0.pcd")
    PCL_ADD_TEST(feature_invariants_estimation test_invariants_estimation
                 FILES test_invariants_estimation.cpp
                 LINK_WITH pcl_gtest pcl_features pcl_io
                 ARGUMENTS "${PCL_SOURCE_DIR}/test/bun0.pcd")
    PCL_ADD_TEST(feature_board_estimation test_board_estimation
                 FILES test_board_estimation.cpp
                 LINK_WITH pcl_gtest pcl_features pcl_io
                 ARGUMENTS "${PCL_SOURCE_DIR}/test/bun0.pcd")
    PCL_ADD_TEST(feature_shot_lrf_estimation test_shot_lrf_estimation
                 FILES test_shot_lrf_estimation.cpp
                 LINK_WITH pcl_gtest pcl_features pcl_io
                 ARGUMENTS "${PCL_SOURCE_DIR}/test/bun0.pcd")
    PCL_ADD_TEST(features_narf test_narf
                 FILES test_narf.cpp
                 LINK_WITH pcl_gtest pcl_features ${FLANN_LIBRARIES})
    PCL_ADD_TEST(a_ii_normals_test test_ii_normals
                 FILES test_ii_normals.cpp
                 LINK_WITH pcl_gtest pcl_io pcl_features
                 ARGUMENTS "${PCL_SOURCE_DIR}/test/table_scene_mug_stereo_textured.pcd")
    PCL_ADD_TEST(feature_moment_of_inertia_estimation test_moment_of_inertia_estimation
                 FILES test_moment_of_inertia_estimation.cpp
                 LINK_WITH pcl_gtest pcl_io pcl_features
                 ARGUMENTS "${PCL_SOURCE_DIR}/test/lamppost.pcd")
    PCL_ADD_TEST(feature_rops_estimation test_rops_estimation
                 FILES test_rops_estimation.cpp
                 LINK_WITH pcl_gtest pcl_io pcl_features
                 ARGUMENTS "${PCL_SOURCE_DIR}/test/rops_cloud.pcd" "${PCL_SOURCE_DIR}/test/rops_indices.txt" "${PCL_SOURCE_DIR}/test/rops_triangles.txt")
    PCL_ADD_TEST(feature_organized_edge_detection test_organized_edge_detection
                 FILES test_organized_edge_detection.cpp
                 LINK_WITH pcl_gtest pcl_io pcl_features pcl_common
                 ARGUMENTS "${PCL_SOURCE_DIR}/test/organized_edge_1.pcd" "${PCL_SOURCE_DIR}/test/organized_edge_2.pcd" "${PCL_SOURCE_DIR}/test/organized_edge_3.pcd")
    PCL_ADD_TEST(feature_normal_estimation_fast_edge_aware test_normal_estimation_fast_edge_aware
                 FILES test_normal_estimation_fast_edge_aware.cpp
                 LINK_WITH pcl_gtest pcl_io pcl_features pcl_common
                 ARGUMENTS "${PCL_SOURCE_DIR}/test/organized_edge_1.pcd" "${PCL_SOURCE_DIR}/test/organized_edge_2.pcd" "${PCL_SOURCE_DIR}/test/organized_edge_3.pcd")
    if (BUILD_keypoints)
      PCL_ADD_TEST(feature_brisk test_brisk
                   FILES test_brisk.cpp
                   LINK_WITH pcl_gtest pcl_io pcl_kdtree pcl_filters pcl_keypoints pcl_common pcl_features pcl_search
                   ARGUMENTS "${PCL_SOURCE_DIR}/test/brisk_image_gt.pcd" "${PCL_SOURCE_DIR}/test/brisk_keypoints_gt.pcd" "${PCL_SOURCE_DIR}/test/brisk_descriptors_gt.pcd")
    endif (BUILD_keypoints)
  endif (BUILD_io)
endif (build)

