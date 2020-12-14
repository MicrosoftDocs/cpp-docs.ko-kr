---
description: '자세히 알아보기: Xcode와 Visual Studio 간에 변경 내용 동기화'
title: Xcode와 Visual Studio 간에 변경 내용 동기화
ms.date: 10/17/2019
ms.assetid: c71a4d7c-120e-4559-a114-3a99c4b860a9
ms.openlocfilehash: 60ce41e41f5b6a2a9f877501eaef0d84306dde07
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97229056"
---
# <a name="sync-changes-between-xcode-and-visual-studio"></a>Xcode와 Visual Studio 간에 변경 내용 동기화

Visual Studio의 C++를 사용한 모바일 개발 구성 요소에는 PC와 Mac 간에 작업을 동기화하는 원격 기능이 포함되어 있습니다. Visual Studio 컴퓨터와 Mac 컴퓨터를 쌍으로 연결하면 Xcode에서 프로젝트를 열고, Xcode와 Visual Studio 간에 코드를 이동하고, 임시 Xcode 프로젝트 디렉터리를 정리하는 데 사용할 수 있는 새 옵션을 Visual Studio의 iOS 애플리케이션에서 사용할 수 있습니다.

원격 컴퓨터 옵션을 사용하려면 프로젝트가 iOS 애플리케이션 프로젝트여야 하며 Visual Studio를 Mac과 쌍으로 연결해야 합니다. Mac을 페어링 하는 방법에 대 한 필수 구성 요소 및 지침은 [iOS를 사용 하 여 빌드할 도구 설치 및 구성](../cross-platform/install-and-configure-tools-to-build-using-ios.md)을 참조 하세요.

## <a name="the-remote-machine-menu"></a>원격 컴퓨터 메뉴

**솔루션 탐색기** 에서 iOS 애플리케이션 프로젝트를 마우스 오른쪽 단추로 클릭하여 상황에 맞는 메뉴를 표시합니다. **원격 컴퓨터** 항목을 선택하여 사용 가능한 원격 옵션을 표시합니다.

![솔루션 탐색기의 원격 컴퓨터 메뉴 항목](../cross-platform/media/cppmdd-u2-remotemachine-menu.jpg "솔루션 탐색기의 원격 컴퓨터 메뉴 항목")

이러한 명령을 사용하면 Xcode에서 프로젝트를 열고, Visual Studio와 Xcode 간에 로컬 변경 내용 또는 전체 프로젝트를 이동하고, 원격 컴퓨터에서 임시 파일을 정리할 수 있습니다.

## <a name="open-in-xcode"></a>Xcode에서 열기

Visual Studio에서 Xcode의 프로젝트를 열려면 **원격 컴퓨터** 하위 메뉴의 **Xcode에서 열기** 를 선택 하 여 쌍을 이루는 원격 컴퓨터에서 선택한 프로젝트를 엽니다. `vcremote` 서버를 사용하여 Mac에서 Xcode를 열고 프로젝트의 복사본이 포함되어 있는 Mac에 생성된 임시 디렉터리로 이동합니다. Visual Studio에서 프로젝트에 사용되는 임시 디렉터리를 보여 주는 팝업 대화 상자가 표시됩니다. 원격 컴퓨터에서 수행하는 작업은 Visual Studio의 **출력** 창에도 표시됩니다. 이러한 작업을 확인하려면 **출력** 창 위쪽의 **출력 보기 선택** 드롭다운에서 **Visual C++ 원격 컴퓨터** 를 선택해야 할 수 있습니다.

![원격 컴퓨터 작업이 표시되는 출력 창](../cross-platform/media/cppmdd-u2-remotemachine-output.png "출력 창에 원격 컴퓨터 작업이 표시 됩니다.")

Mac에서는 모든 Xcode 도구를 사용하여 코드/리소스, 스토리보드 및 작업을 편집할 수 있습니다. Visual Studio에서 iOS 애플리케이션 프로젝트는 원격 컴퓨터에서 변경을 수행했을 수 있음을 나타내기 위해 "Xcode에서 열림" 주석이 지정됩니다. 편집이 완료되면 원격에서 끌어오기 또는 원격에서 증분 끌어오기 명령을 사용하여 변경 내용을 Visual Studio 프로젝트로 다시 복사할 수 있습니다.

## <a name="push-to-remote-and-incremental-push-to-remote"></a>원격에 푸시 및 원격에 증분 푸시

Visual Studio에서 iOS 애플리케이션 프로젝트를 변경한 경우 원격에 푸시 및 원격에 증분 푸시 명령을 사용하여 변경된 프로젝트 파일을 쌍으로 연결된 원격 컴퓨터로 이동할 수 있습니다. 원격에 푸시 명령은 모든 프로젝트 파일을 원격 컴퓨터로 복사합니다. 원격에 증분 푸시 명령은 변경된 파일만 원격 컴퓨터로 복사합니다. 많이 변경되지 않는 대규모 프로젝트의 경우 증분 명령을 사용하면 시간과 대역폭을 절약할 수 있습니다.

프로젝트 파일을 Mac으로 복사하려면 Visual Studio의 **솔루션 탐색기** 에서 iOS 애플리케이션 프로젝트를 마우스 오른쪽 단추로 클릭하여 상황에 맞는 메뉴를 엽니다. **원격 컴퓨터** 를 선택하고 **원격에 푸시** 또는 **원격에 증분 푸시** 중 하나를 선택하여 프로젝트 파일을 Visual Studio에서 Mac으로 복사합니다.

## <a name="pull-from-remote-and-incremental-pull-from-remote"></a>원격에서 끌어오기 및 원격에서 증분 끌어오기

Xcode에서 프로젝트를 변경한 후에는 Visual Studio로 변경 내용을 다시 이동하여 프로젝트를 동기화 상태로 유지합니다.

프로젝트 파일을 Mac에서 복사하려면 Visual Studio의 **솔루션 탐색기** 에서 iOS 애플리케이션 프로젝트를 마우스 오른쪽 단추로 클릭하여 상황에 맞는 메뉴를 엽니다. **원격 컴퓨터** 를 선택하고 **원격에서 끌어오기** 또는 **원격에서 증분 끌어오기** 중 하나를 선택하여 프로젝트 파일을 Mac에서 Visual Studio로 복사합니다.

## <a name="clean-remote"></a>원격 정리

원격 정리 명령을 사용하면 원격 컴퓨터에서 임시 프로젝트 디렉터리의 파일을 삭제할 수 있습니다. 이 경우 소스 파일이나 빌드 프로젝트를 비롯한 디렉터리의 콘텐츠가 Mac에서 제거됩니다. 원격 정리 명령을 사용하기 전에 원격에서 끌어오기 또는 원격에서 증분 끌어오기를 사용하여 유지하려는 변경 내용을 Visual Studio로 다시 동기화했는지 확인하세요.

원격 머신에서 임시 프로젝트 디렉터리를 정리하려면 Visual Studio의 **솔루션 탐색기** 에서 iOS 애플리케이션 프로젝트를 마우스 오른쪽 단추로 클릭하여 상황에 맞는 메뉴를 엽니다. **원격 컴퓨터** 를 선택하고 **원격 정리** 를 선택하여 Mac에서 프로젝트 디렉터리 파일을 제거합니다.
