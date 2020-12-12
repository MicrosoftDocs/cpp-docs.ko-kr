---
description: 다음에 대 한 자세한 정보:/APPCONTAINER (Microsoft Store 앱)
title: /APPCONTAINER (UWP/Microsoft Store 앱)
ms.date: 11/04/2016
ms.assetid: 9a432db5-7640-460b-ab18-6f61fa7daf6f
ms.openlocfilehash: 4cb78c85aa59ebd7fc0eb82af9497606bc3c431c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97179579"
---
# <a name="appcontainer-microsoft-store-app"></a>/APPCONTAINER (Microsoft Store 앱)

링커가 앱 컨테이너에서 실행 해야 하는 실행 가능 이미지를 만들지 여부를 지정 합니다.

## <a name="syntax"></a>구문

```
/APPCONTAINER[:NO]
```

## <a name="remarks"></a>설명

기본적으로/APPCONTAINER는 해제 되어 있습니다.

이 옵션은 응용 프로그램이 appcontainer 프로세스 격리 환경에서 실행 되어야 하는지 여부를 나타내도록 실행 파일을 수정 합니다. Appcontainer 환경에서 실행 해야 하는 응용 프로그램 (예: UWP (유니버설 Windows 플랫폼) 또는 Windows Phone 8.x 앱)에 대해/APPCONTAINER를 지정 합니다. (템플릿에서 유니버설 Windows 앱을 만들 때이 옵션은 Visual Studio에서 자동으로 설정 됩니다.) 데스크톱 앱의 경우/APPCONTAINER: NO를 지정 하거나 옵션을 생략 합니다.

/APPCONTAINER 옵션은 Windows 8에서 도입 되었습니다.

### <a name="to-set-this-linker-option-in-visual-studio"></a>Visual Studio에서 이 링커 옵션을 설정하려면

1. 프로젝트 **속성 페이지** 대화 상자를 엽니다. 자세한 정보는 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조하세요.

1. **구성 속성** 노드를 확장합니다.

1. **링커** 노드를 확장합니다.

1. **명령줄** 속성 페이지를 선택 합니다.

1. **추가 옵션** 에서 또는를 `/APPCONTAINER` 입력 `/APPCONTAINER:NO` 합니다.

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)
