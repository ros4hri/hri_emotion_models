# Copyright (c) 2024 PAL Robotics S.L. All rights reserved.
#
# Unauthorized copying of this file, via any medium is strictly prohibited,
# unless it was supplied under the terms of a license agreement or
# nondisclosure agreement with PAL Robotics SL. In this case it may not be
# copied or disclosed except in accordance with the terms of that agreement.

cmake_minimum_required(VERSION 3.8)
project(hri_emotion_models)

install(
  DIRECTORY models
  DESTINATION share/${PROJECT_NAME}
)

# (manually) register the resource in ament_index
# equivalent to:
# ament_index_register_resource("dnn_models.emotion_recognition" CONTENT "models/emotion-ferplus-8.onnx")
file(WRITE ${CMAKE_CURRENT_BINARY_DIR}/${PROJECT_NAME} "models/emotion-ferplus-8.onnx")
install(FILES ${CMAKE_CURRENT_BINARY_DIR}/${PROJECT_NAME} DESTINATION share/ament_index/resource_index/dnn_models.emotion_recognition/)
