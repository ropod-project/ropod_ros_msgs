cmake_minimum_required(VERSION 2.8.6)
project(ropod_ros_msgs)

find_package(catkin REQUIRED COMPONENTS message_generation std_msgs geometry_msgs genmsg actionlib_msgs actionlib)

add_message_files(
   DIRECTORY elevators
   FILES
   ElevatorRequest.msg
   ElevatorRequestReply.msg
   ElevatorRobotConfirmation.msg
)

add_message_files(
   DIRECTORY robot
   FILES
   RobotStatus.msg
   SmartWheelData.msg
   SmartWheelInputData.msg
   SmartWheelOutputData.msg
   SmartWheelCommand.msg
   SmartWheelCommandList.msg
)

add_message_files(
   DIRECTORY task
   FILES
   Action.msg
   Elevator.msg
   RobotAction.msg
   RobotTask.msg
   RobotTaskUpdate.msg
   Task.msg
   TaskRequest.msg
   TaskProgressGOTO.msg
   TaskProgressDOCK.msg
   TaskProgressELEVATOR.msg
   Status.msg
)

add_message_files(
   DIRECTORY world_model
   FILES
   Area.msg
   SubArea.msg
   Position.msg
   Shape.msg
   DoorDetection.msg
   NavigationArea.msg
   Waypoint.msg
   PathPlan.msg
   BlockedConnection.msg
   Side.msg
   KeyValue.msg
   Object.msg
   ObjectList.msg
)


add_message_files(
   DIRECTORY experiments
   FILES
   Transition.msg
   TransitionList.msg
)

add_message_files(
  DIRECTORY monitoring
  FILES
  StateInfo.msg
  Event.msg
)

add_message_files(
   DIRECTORY docking
   FILES
   DockingCommand.msg
   DockingFeedback.msg
)

add_action_files(
  DIRECTORY action
  FILES
  RoutePlanner.action
  GetTopologyNode.action
  GetShape.action
  GetPathPlan.action
  GetElevatorWaypoints.action
  GetNearestWLAN.action
  ExecuteExperiment.action
  GetObjects.action
  GetDockingPose.action
  GoTo.action
  Dock.action
  NavElevator.action
)

add_service_files(
  DIRECTORY srv
  FILES
  GetDoorStatus.srv
  ToggleObjectPublisher.srv
)

generate_messages(
  DEPENDENCIES
  std_msgs
  geometry_msgs
  actionlib_msgs
)

catkin_package(
#  INCLUDE_DIRS include
   CATKIN_DEPENDS message_runtime roscpp std_msgs geometry_msgs actionlib_msgs
#  DEPENDS message_runtime
)
