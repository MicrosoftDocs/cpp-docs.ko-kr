---
description: '자세한 정보: c + +를 사용한 플랫폼 간 모바일 개발'
title: C++를 사용하여 플랫폼 간 모바일 개발
ms.date: 11/14/2019
ms.assetid: 0bb872d6-981b-4c96-9143-fcec5336bf0d
ms.openlocfilehash: 98e7124ca8a687a2308a97eb11da80fc0c69483a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97213236"
---
# <a name="cross-platform-mobile-development-with-c"></a>C++를 사용하여 플랫폼 간 모바일 개발

Visual Studio에서 사용할 수 있는 플랫폼 간 도구를 사용하여 iOS, Android 및 Windows 디바이스용 네이티브 C++ 앱을 빌드할 수 있습니다. **C++를 사용한 모바일 개발** 은 Visual Studio 설치 관리자에서 사용할 수 있는 워크로드입니다. 이 워크로드는 공유 라이브러리 및 네이티브 앱의 플랫폼 간 개발에 필요한 SDK와 도구를 설치합니다. 개발 환경이 설치된 후 C++를 사용하여 iOS 및 Android 디바이스와 플랫폼, Windows, Windows 스토어 및 Xbox에서 실행되는 코드를 만들 수 있습니다.

여러 플랫폼을 위한 코드를 작성하기가 어려울 수 있습니다. iOS, Android 및 Windows용 기본 개발 언어와 도구는 각 플랫폼마다 다릅니다. 그러나 모든 플랫폼이 C++의 코드 작성을 지원합니다. 이는 여러 플랫폼에 핵심 코드를 다시 사용할 수 있도록 하는 공통 분모입니다. C++로 작성된 네이티브 코드는 성능과 리버스 엔지니어링 방지 기능이 둘 다 뛰어날 수 있습니다. 여러 플랫폼용 앱을 만들 때 코드 재사용을 통해 시간과 노력을 모두 절약할 수 있습니다.

플랫폼 간 모바일 개발용 C++를 사용하여 개발하는 경우 다음과 같은 여러 이점이 있습니다.

- **간편한 설치.** Visual Studio 설치 관리자는 Android 및 iOS용 앱 또는 라이브러리를 빌드하는 데 필요한 타사 도구 및 SDK를 가져오고 설치합니다. 구성 및 설정이 간단하며 대부분 자동입니다.

- **강력하고 친숙한 빌드 환경.** Visual Studio 템플릿을 사용하여 공유 가능한 플랫폼 간 솔루션 및 프로젝트를 쉽게 만듭니다. 하나의 공통 인터페이스를 사용하여 모든 프로젝트에 대한 속성을 관리합니다. Visual Studio 편집기에서 모든 코드를 편집하고 코드 완성 및 오류 강조 표시를 위해 기본 제공 플랫폼 간 IntelliSense를 활용합니다.

- **통합된 디버깅 환경.** Visual Studio의 세계적인 수준의 디버깅 도구를 사용 하 여 모든 플랫폼 (Android 장치 및 에뮬레이터, iOS 시뮬레이터 및 장치, Windows 또는 Windows 스토어 장치 및 에뮬레이터)에서 c + + 코드를 시청 하 고 단계별로 실행 합니다.

## <a name="get-the-tools"></a>도구 얻기

C++를 사용한 모바일 개발은 Visual Studio와 함께 제공되는 설치 가능한 워크로드입니다. 필수 조건과 설치 지침은 [C++를 사용한 플랫폼 간 모바일 개발 설치](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md)를 참조하세요. iOS용 코드를 빌드하려면 Mac 컴퓨터와 Apple iOS 개발자 계정도 필요합니다. 자세한 내용은 [iOS를 사용 하 여 빌드할 도구 설치 및 구성](../cross-platform/install-and-configure-tools-to-build-using-ios.md)을 참조 하세요.

## <a name="come-up-to-speed"></a>속도 개선

Android 또는 iOS 개발에서 전환하는 경우 시작 방법에 대한 훌륭한 자료가 있습니다. Visual Studio는 표현 능력과 기능을 갖춘 개발 환경입니다. 사용 방법을 알아보려면 [Android 개발자를 위한 시작](/previous-versions/windows/apps/dn275875\(v=win.10\)) 또는 [iOS 개발자를 위한 시작](/previous-versions/windows/apps/jj657966\(v=win.10\))을 참조하세요. 이 문서에서는 Windows 및 Windows 스토어용 플랫폼 간 앱을 개발하는 데 필요한 개념과 Visual Studio를 소개합니다. IOS 및 Android 용 첫 플랫폼 간 앱 작성을 시작 하려면 [Android 및 iOS에서 OPENGL ES 응용 프로그램 빌드](../cross-platform/build-an-opengl-es-application-on-android-and-ios.md)를 참조 하세요.

C++를 사용한 플랫폼 간 모바일 개발에는 앱에서 시작하는 데 도움이 되는 여러 템플릿이 포함되어 있습니다.

- Native-Activity 애플리케이션(Android)

  전체 C++ OpenGL 앱을 Android Native Activity 프로젝트로 만듭니다.

- OpenGLES 애플리케이션(Android, iOS)

  Android Native Activity 앱과 iOS 앱 둘 다를 빌드하는 프로젝트 집합이 포함된 솔루션을 만듭니다. 이러한 앱은 공통 OpenGL ES C++ 코드로 만들어진 플랫폼별 라이브러리를 사용하여 각 앱에 동일한 회전 큐브를 그립니다.

- 공유 라이브러리(Android, iOS)

  공유 프로젝트의 공통 C++ 코드를 사용하여 Android 동적 라이브러리(.so) 파일 및 iOS 정적 라이브러리(.a) 파일을 만드는 프로젝트가 포함된 솔루션을 만듭니다.

- 기본 애플리케이션(Android, Ant)

  Java 소스 코드와 Ant 빌드 시스템만 사용하는 Android "Hello, World" 앱 프로젝트를 만듭니다.

- 기본 애플리케이션(Android, Gradle)

  Java 소스 코드와 Gradle 빌드 시스템만 사용하는 Android "Hello, World" 앱 프로젝트를 만듭니다.

- 기본 라이브러리(Android, Ant)

  Java 소스 코드와 Ant 빌드 시스템만 사용하는 Android "Hello, World" 라이브러리 프로젝트를 만듭니다.

- 기본 라이브러리(Android, Gradle)

  Java 소스 코드와 Gradle 빌드 시스템만 사용하는 Android "Hello, World" 라이브러리 프로젝트를 만듭니다.

- 동적 공유 라이브러리(Android)

  C++ 코드를 사용하여 Android 동적 라이브러리(.so) 파일을 만듭니다.

- OpenGLES 2 애플리케이션(iOS)

  OpenGL ES 2 iOS 앱을 빌드하기 위한 프로젝트 집합이 포함된 솔루션을 만듭니다. 이 앱은 C++ OpenGL ES 코드 라이브러리를 사용하여 iOS 앱에서 회전하는 직육면체를 그립니다. 이 앱을 토대로 하여 iOS 앱으로 C++ 라이브러리를 가져오는 방법을 파악할 수 있습니다.

- 정적 라이브러리(Android)

  Android용 정적 라이브러리를 빌드하는 프로젝트를 만듭니다. Android 앱에서 하나의 동적 라이브러리만 연결할 수 있지만 정적 라이브러리는 개수에 관계없이 연결할 수 있습니다.

- 정적 라이브러리(iOS)

  iOS용 정적 라이브러리를 빌드하는 프로젝트를 만듭니다.

- 메이크파일 프로젝트(Android)

  사용자 고유의 Android 메이크파일 프로젝트에 대한 프로젝트 래퍼를 만듭니다.

## <a name="try-out-sample-code"></a>샘플 코드 체험

Windows, Android 및 iOS 앱에서 사용할 수 있는 공유 코드 라이브러리를 만드는 방법을 보여 주는 샘플을 다운로드합니다. Android용 전체 Native Activity 앱을 만드는 방법의 예도 참조하세요. 시작 하려면 [플랫폼 간 모바일 개발 예](../cross-platform/cross-platform-mobile-development-examples.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[C + +를 사용 하 여 플랫폼 간 모바일 개발 설치](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md)\
[IOS를 사용 하 여 빌드할 도구 설치 및 구성](../cross-platform/install-and-configure-tools-to-build-using-ios.md)\
[Android native activity 앱 만들기](../cross-platform/create-an-android-native-activity-app.md)\
[Android 및 iOS에서 OpenGL ES 응용 프로그램 빌드](../cross-platform/build-an-opengl-es-application-on-android-and-ios.md)\
[플랫폼 간 모바일 개발 예제](../cross-platform/cross-platform-mobile-development-examples.md)
