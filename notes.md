- modify build.sh to build.ps1 and do a ton of stuff manually
- install vcpkg, install Eigen3:x64-windows with
- solve no min and max in /Thirdparty/g2o/g2o/core/optimization_algorithm_factory.cpp by including algorithm
- add asprintf.h to /stuff bc it does not exist on Windows (or most platforms)
- add /winutils and files in it
- add unistd.h to /include
- remove /src/Optimizer.cc(2210) (f_lba.close();)
- add add_definitions(/bigobj) on CmakeLists.txt(125?)
- include <winutil/getopt.h> in /Examples/Monocular/mono_euroc.cc, /Examples/Monocular-Inertial/mono_inertial_tum_vi.cc, /Examples/Monocular-Inertial/mono_kitti.cc, /Examples/Monocular/mono_tum.cc, /Examples/Monocular/mono_tum_vi.cc, /Examples/RGB-D/rgbd_tum.cc, /Examples/Stereo/stereo_euroc.cc, /Examples/Stereo-Inertial/stereo_euroc.cc, /Examples/Stereo-Inertial/stereo_inertial_tum_vi.cc, /Examples/Stereo/stereo_kitti.cc, /Examples/Stereo/stereo_tum_vi.cc
- copy ..\Thirdparty\DBoW2\lib\Release\DBoW2.lib to ..\Thirdparty\DBoW2\lib\DBoW2.lib
- copy Thirdparty\g2o\bin\Release\g2o.lib to Thirdparty\g2o\lib\g2o.lib
- built ORB_SLAM3 (not ALL_BUILD, examples fail)

msbuild .\mono_euroc.vcxproj /p:StopOnFirstFailure=true /p:Configuration=Release
>>
"D:\Users\Kevin-User\Documents\GitHub\ORB_SLAM3\build\mono_euroc.vcxproj" (default target) (1) ->
(Link target) ->
  ORB_SLAM3.lib(System.obj) : error LNK2005: "void __cdecl usleep(unsigned long)" (?usleep@@YAXK@Z) already defined in mono_euroc.obj [D:\Users\Kevin-User\Documents\GitHub\ORB_SLAM3\build\mono_euroc.vcxproj]
  ORB_SLAM3.lib(Atlas.obj) : error LNK2005: "void __cdecl usleep(unsigned long)" (?usleep@@YAXK@Z) already defined in mono_euroc.obj [D:\Users\Kevin-User\Documents\GitHub\ORB_SLAM3\build\mono_euroc.vcxproj]
  ORB_SLAM3.lib(Viewer.obj) : error LNK2005: "void __cdecl usleep(unsigned long)" (?usleep@@YAXK@Z) already defined in mono_euroc.obj [D:\Users\Kevin-User\Documents\GitHub\ORB_SLAM3\build\mono_euroc.vcxproj]
  ORB_SLAM3.lib(LoopClosing.obj) : error LNK2005: "void __cdecl usleep(unsigned long)" (?usleep@@YAXK@Z) already defined in mono_euroc.obj [D:\Users\Kevin-User\Documents\GitHub\ORB_SLAM3\build\mono_euroc.vcxproj]
  ORB_SLAM3.lib(LocalMapping.obj) : error LNK2005: "void __cdecl usleep(unsigned long)" (?usleep@@YAXK@Z) already defined in mono_euroc.obj [D:\Users\Kevin-User\Documents\GitHub\ORB_SLAM3\build\mono_euroc.vcxproj]
  ORB_SLAM3.lib(Tracking.obj) : error LNK2005: "void __cdecl usleep(unsigned long)" (?usleep@@YAXK@Z) already defined in mono_euroc.obj [D:\Users\Kevin-User\Documents\GitHub\ORB_SLAM3\build\mono_euroc.vcxproj]
  LINK : fatal error LNK1104: cannot open file 'libboost_serialization-vc100-mt-1_46_1.lib' [D:\Users\Kevin-User\Documents\GitHub\ORB_SLAM3\build\mono_euroc.vcxproj]