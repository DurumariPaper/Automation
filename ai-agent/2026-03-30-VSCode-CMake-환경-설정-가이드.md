### Context
CLion과 같은 통합 개발 환경(IDE)에서 제공하는 편리한 CMake 빌드 환경에 익숙한 개발자가 Visual Studio Code(VS Code)로 IDE를 전환할 경우, CMake 프로젝트 빌드 과정에서 불편함을 느낄 수 있습니다. 본 문서는 VS Code에서 CMake 프로젝트를 효율적으로 설정하고 빌드하는 방법에 대한 가이드라인을 제공하여, CLion에 준하는 편리한 개발 경험을 구축할 수 있도록 돕습니다.

### Core
VS Code에서 CMake 프로젝트를 관리하고 빌드하는 가장 효과적인 방법은 공식적으로 지원하는 **CMake Tools** 확장(extension)을 사용하는 것입니다. 이 확장은 CMake 프로젝트를 자동으로 감지하고, 빌드, 구성, 디버깅 기능을 통합하여 제공합니다.

*   **CMake Tools 확장 설치**:
    VS Code 마켓플레이스에서 "CMake Tools"를 검색하여 설치합니다. 이 확장은 CMake, C/C++ 확장과 함께 작동하여 최적의 환경을 제공합니다.

*   **CMake 프로젝트 열기**:
    VS Code에서 `CMakeLists.txt` 파일이 포함된 프로젝트 폴더를 엽니다. CMake Tools 확장이 이를 자동으로 감지하고, 하단 상태 표시줄에 CMake 관련 옵션들이 나타납니다.

*   **CMake 구성 (Configure)**:
    프로젝트를 처음 열거나 `CMakeLists.txt` 파일이 변경되면, CMake Tools는 자동으로 프로젝트를 구성(configure)하려 시도합니다. 만약 수동으로 구성해야 한다면, VS Code 명령 팔레트(`Ctrl+Shift+P` 또는 `Cmd+Shift+P`)를 열고 `CMake: Configure`를 입력하여 실행할 수 있습니다. 이 과정에서 빌드 시스템(예: Makefiles, Ninja)과 컴파일러(예: GCC, Clang)를 선택하게 됩니다.

*   **CMake 빌드 (Build)**:
    구성 완료 후, VS Code 상태 표시줄의 빌드 아이콘(망치 모양)을 클릭하거나 명령 팔레트에서 `CMake: Build`를 실행하여 프로젝트를 빌드할 수 있습니다. 특정 대상을 빌드하려면 `CMake: Build Target`을 사용합니다.

*   **디버깅 (Debug)**:
    CMake Tools는 `launch.json` 파일을 자동으로 생성하거나 업데이트하여 디버깅 설정을 지원합니다. 빌드된 실행 파일을 선택하고 디버깅 뷰에서 `Run and Debug`를 시작하여 프로그램을 디버깅할 수 있습니다.

*   **추가 설정 (`settings.json`)**:
    프로젝트별 또는 전역 설정을 위해 `.vscode/settings.json` 파일을 활용할 수 있습니다. 예를 들어, 기본 빌드 경로를 지정하거나, 특정 CMake 옵션을 전달할 수 있습니다.

    ```cmake
    # CMakeLists.txt 예시
    cmake_minimum_required(VERSION 3.10)
    project(MyProject CXX)

    add_executable(my_app main.cpp)
    ```
    ```json
    // settings.json 예시
    // .vscode/settings.json 파일에 저장
    {
        "cmake.buildDirectory": "${workspaceFolder}/build",
        "cmake.generator": "Ninja",
        "cmake.configureSettings": {
            "CMAKE_BUILD_TYPE": "Debug"
        }
    }
    ```

### Insight
VS Code의 CMake Tools 확장은 CLion이 제공하는 통합 CMake 경험과 유사하게, 설정(Configuration), 빌드(Build), 디버깅(Debugging) 과정을 효과적으로 통합하여 개발 흐름을 간소화합니다. 자동 감지 및 명령 팔레트를 통한 손쉬운 접근은 빌드 시스템에 대한 깊은 이해 없이도 빠르게 프로젝트를 시작하고 관리할 수 있게 해줍니다. 특히, `settings.json`을 통한 유연한 설정은 다양한 프로젝트 요구사항에 맞춰 빌드 환경을 최적화할 수 있는 강력한 이점을 제공합니다. 이러한 기능들을 통해 개발자는 빌드 환경 설정에 드는 시간을 절약하고 핵심 개발 작업에 집중할 수 있습니다.

**출처:**
*   [Using CMake Tools in VS Code](https://code.visualstudio.com/docs/cpp/cmake-linux)
*   [CMake Tools for Visual Studio Code](https://github.com/microsoft/vscode-cmake-tools)