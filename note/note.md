### note

## 1 package

src/
├── CMakeLists.txt -> /opt/ros/noetic/share/catkin/cmake/toplevel.cmake
├── planner
│   ├── bspline_opt B样条优化
│   ├── drone_detect 无人机检测
│   ├── path_searching 路径搜索
│   ├── plan_env 规划环境
│   ├── plan_manage 规划管理
│   ├── rosmsg_tcp_bridge 协议桥接
│   └── traj_utils 可视化工具，多项式
└── uav_simulator
    ├── fake_drone 无人机外观模型
    ├── local_sensing 局部感知
    ├── map_generator 地图生成
    ├── mockamap 地图生成库
    ├── so3_control so3控制器
    ├── so3_quadrotor_simulator 无人机仿真
    └── Utils
        ├── cmake_utils cmake工具
        ├── multi_map_server 多地图生成
        ├── multi_map_server.zip
        ├── odom_visualization 里程计可视化
        ├── pose_utils 位姿数据结构
        ├── quadrotor_msgs 四旋翼数据结构
        ├── rviz_plugins rviz插件
        ├── uav_utils 无人机数据结构
        └── waypoint_generator 路径点生成

## 2 node

![Alt text](rosgraph.svg)
/ramdom_forest 地图生成
/pcl_render_node 点云读取

/ego_planner_node 规划器
/traj_server 轨迹服务器
/poscmd_to_odom 基于规划路径的里程计
/odom_visulization odom可视化

## 3 planner 

### 3.1 状态机

class EGOReplanFSM

// 读取参数
flight_type target输入方法
fsm/waypoint target路径点

enum FSM_EXEC_STATE
    {
      INIT, //
      WAIT_TARGET,
      GEN_NEW_TRAJ,
      REPLAN_TRAJ,
      EXEC_TRAJ,
      EMERGENCY_STOP,
      SEQUENTIAL_START
    };

