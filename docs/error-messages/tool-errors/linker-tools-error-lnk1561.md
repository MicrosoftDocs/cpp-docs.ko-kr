---
description: '자세한 정보: 링커 도구 오류 LNK1561'
title: 링커 도구 오류 LNK1561
ms.date: 11/04/2016
f1_keywords:
- LNK1561
helpviewer_keywords:
- LNK1561
ms.assetid: cb0b709b-7c9c-4496-8a4e-9e1e4aefe447
ms.openlocfilehash: b8c99c6e4b016b1eee443cf8f166665f4f9ad894
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97310649"
---
# <a name="linker-tools-error-lnk1561"></a>링커 도구 오류 LNK1561

진입점을 정의 해야 합니다.

링커가 실행 파일에서 호출 하는 초기 함수인 *진입점* 을 찾지 못했습니다. 기본적으로 링커는 콘솔 앱에 대 한 `main` 또는 `wmain` 함수, `WinMain` `wWinMain` Windows 앱에 대 한 또는 함수 또는 `DllMain` 초기화가 필요한 DLL을 찾습니다. [/Entry](../../build/reference/entry-entry-point-symbol.md) 링커 옵션을 사용 하 여 다른 함수를 지정할 수 있습니다.

이 오류는 다음과 같은 여러 원인이 있을 수 있습니다.

- 연결할 파일 목록에서 진입점을 정의 하는 파일을 포함 하지 않았을 수 있습니다. 진입점 함수를 포함 하는 파일이 앱에 연결 되어 있는지 확인 합니다.
- 잘못 된 함수 시그니처를 사용 하 여 진입점을 정의 했을 수 있습니다. 예를 들어 함수 이름에 대해 잘못 된 사례를 사용 하거나 잘못 된 사례를 사용 했거나 반환 형식 또는 매개 변수 형식을 잘못 지정 했을 수 있습니다.
- DLL을 빌드할 때 [/dll](../../build/reference/dll-build-a-dll.md) 옵션을 지정 하지 않았을 수 있습니다.
- [/Entry](../../build/reference/entry-entry-point-symbol.md) 링커 옵션을 사용할 때 진입점 함수 이름을 잘못 지정 했을 수 있습니다.
- [LIB](../../build/reference/lib-reference.md) 도구를 사용 하 여 DLL을 빌드하는 경우 .def 파일을 지정 했을 수 있습니다. 그럴 경우 빌드에서 .def 파일을 제거 합니다.

앱을 빌드할 때 링커는를 호출 하 여 코드를 시작 하는 진입점 함수를 찾습니다. 이 함수는 앱이 로드 되 고 런타임이 초기화 된 후 호출 되는 함수입니다. 앱에 대 한 진입점 함수를 제공 해야 합니다. 그렇지 않으면 앱을 실행할 수 없습니다. 진입점은 DLL의 경우 선택 사항입니다. 기본적으로 링커는와 같은 여러 특정 이름 및 서명 중 하나가 있는 진입점 함수를 찾습니다 `int main(int, char**)` . /ENTRY 링커 옵션을 사용 하 여 진입점으로 다른 함수 이름을 지정할 수 있습니다.

## <a name="example"></a>예제

다음 샘플에서는 LNK1561를 생성 합니다.

```cpp
// LNK1561.cpp
// LNK1561 expected
int i;
// add a main function to resolve this error
```
