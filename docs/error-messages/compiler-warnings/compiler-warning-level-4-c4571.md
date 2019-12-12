---
title: 컴파일러 경고(수준 4) C4571
ms.date: 11/04/2016
f1_keywords:
- C4571
helpviewer_keywords:
- C4571
ms.assetid: 07aa17bd-b15c-4266-824c-57cc445e8edd
ms.openlocfilehash: 3a8f2093e90f8a681d171e19e2b8a066546f8684
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990664"
---
# <a name="compiler-warning-level-4-c4571"></a>컴파일러 경고(수준 4) C4571

알림: Visual C++ 7.1 이후에 catch (...) 의미 체계가 변경 되었습니다. 구조적 예외 (SEH)는 더 이상 catch 되지 않습니다.

**/EHs**를 사용 하 여 컴파일할 때 모든 catch (...) 블록에 대해 C4571이 생성 됩니다.

**/EHs**를 사용 하 여 컴파일할 때 catch (...) 블록은 구조적 예외를 catch 하지 않습니다 (예: 0으로 나누기, null 포인터). catch (...) 블록은 명시적으로 throw 된 예외를 C++ catch 합니다.  자세한 내용은 [예외 처리](../../cpp/exception-handling-in-visual-cpp.md)를 참조하세요.

기본적으로 이 경고는 해제되어 있습니다.  **/EHs** 를 사용 하 여 컴파일할 때 catch (...) 블록이 구조화 된 예외를 catch 하지 않도록 하려면이 경고를 설정 합니다.  자세한 내용은 [기본적으로 해제되어 있는 컴파일러 경고](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 를 참조하세요.

다음 방법 중 하나를 수행 하 여 C4571를 해결할 수 있습니다.

- 여전히 catch (...) 블록을 사용 하 여 구조적 예외를 catch 하려면 **/eha** 를 사용 하 여 컴파일합니다.

- Catch (...) 블록이 구조화 된 예외를 catch 하지 않도록 하 고 catch (...) 블록을 계속 사용 하려는 경우에는 C4571을 사용 하지 마십시오.  구조적 예외 처리 키워드 ( **__try**, **__except**및 **__finally**)를 사용 하 여 구조적 예외를 여전히 catch 할 수 있습니다.  그러나 컴파일된 **/EHs** 소멸자는 SEH 예외가 발생할 때가 아니라 C++ 예외가 throw 되는 경우에만 호출 됩니다.

- Catch (...) C++ 블록을 특정 예외에 대 한 catch 블록으로 바꾸고 필요에 따라 C++ 예외 처리 ( **__try**, **__except**및 **__finally**)를 중심으로 구조적 예외 처리를 추가 합니다.  자세한 내용은 [구조적 예외 처리 (CC++/)](../../cpp/structured-exception-handling-c-cpp.md) 를 참조 하세요.

자세한 내용은 [/Ceh (예외 처리 모델)](../../build/reference/eh-exception-handling-model.md) 를 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C4571를 생성 합니다.

```cpp
// C4571.cpp
// compile with: /EHs /W4 /c
#pragma warning(default : 4571)
int main() {
   try {
      int i = 0, j = 1;
      j /= i;   // this will throw a SE (divide by zero)
   }
   catch(...) {}   // C4571 warning
}
```
