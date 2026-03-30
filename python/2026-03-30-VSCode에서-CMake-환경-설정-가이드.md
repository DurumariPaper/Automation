### Context
CLion에서 Visual Studio Code(VS Code)로 개발 환경을 전환하면서 CMake 프로젝트 빌드 과정에 불편함을 겪는 사용자를 위한 가이드입니다. VS Code에서 CMake를 효율적으로 설정하고 사용하는 방법을 제시하여, 기존 IDE의 편리함을 VS Code에서도 경험할 수 있도록 돕습니다.

### Core
VS Code에서 CMake를 사용하려면 'CMake Tools' 확장을 설치하고 프로젝트를 구성해야 합니다. 다음은 기본적인 설정 단계입니다.

*   **1. CMake Tools 확장 설치:**
    VS Code 마켓플레이스에서 'CMake Tools' 확장을 검색하여 설치합니다. 이 확장은 CMake 프로젝트를 구성, 빌드 및 디버깅하는 데 필요한 기능을 제공합니다.

*   **2. 프로젝트 폴더 열기:**
    VS Code에서 CMakeLists.txt 파일이 있는 프로젝트 루트 폴더를 엽니다.

*   **3. 빌드 구성 (Configure):**
    'CMake Tools' 확장은 자동으로 `CMakeLists.txt` 파일을 감지하고 빌드 구성을 제안합니다.
    *   VS Code 하단 상태바에 있는 'Build' 또는 'Configure' 버튼을 클릭하거나, `Ctrl+Shift+P`를 눌러 명령 팔레트를 열고 `CMake: Configure`를 검색하여 실행합니다.
    *   이 과정에서 빌드에 사용할 컴파일러 킷(Kit)을 선택해야 할 수 있습니다 (예: Visual Studio Community 2019 Release - amd64, GCC, Clang 등).

*   **4. 빌드 타겟 선택:**
    하단 상태바에서 빌드할 타겟을 선택합니다. 기본적으로 'all' 또는 프로젝트의 실행 파일 타겟을 선택할 수 있습니다.

*   **5. 프로젝트 빌드:**
    하단 상태바의 'Build' 버튼을 클릭하거나, 명령 팔레트에서 `CMake: Build`를 실행하여 프로젝트를 빌드합니다.
    *   빌드 출력은 터미널 패널에서 확인할 수 있습니다.

*   **예시 CMakeLists.txt:**
    간단한 'Hello World' C++ 프로젝트를 위한 `CMakeLists.txt` 파일 예시입니다.
    ```cmake
    cmake_minimum_required(VERSION 3.10)
    project(HelloWorld CXX)

    add_executable(HelloWorld main.cpp)
    ```

### Insight
VS Code의 'CMake Tools' 확장은 CLion과 유사한 통합 개발 경험을 제공합니다. 특히, 상태바를 통한 직관적인 빌드 및 구성 옵션 접근은 생산성을 크게 향상시킵니다. 컴파일러 킷 선택을 통해 다양한 환경에서의 크로스 플랫폼 개발도 용이하며, `CMakeLists.txt` 파일을 기반으로 자동 구성되므로 설정 오류를 줄일 수 있습니다. 처음에는 설정이 다소 복잡하게 느껴질 수 있으나, 한 번 구성하고 나면 CLion 못지않은 편리함을 제공합니다.

**출처:**
*   [CMake Tools for Visual Studio Code](https://code.visualstudio.com/docs/cpp/cmake-linux)
*   [Getting Started with CMake Tools on Linux](https://vector-of-bool.github.io/2018/08/25/cmake-tools-part1.html)