---
description: '에 대 한 자세한 정보: safebuffers'
title: safebuffer
ms.date: 11/04/2016
f1_keywords:
- safebuffers_cpp
helpviewer_keywords:
- __declspec keyword (C++), safebuffers
- safebuffers __declspec keyword
ms.assetid: 0b0dce14-4523-44d2-8070-5dd0fdabc618
ms.openlocfilehash: 8fefa12ffcbd81d58f4f5002e27751f03d7c1cb9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319354"
---
# <a name="safebuffers"></a>safebuffer

**Microsoft 전용**

함수에 대한 버퍼 오버런 보안 검사를 삽입하지 않도록 컴파일러에 지시합니다.

## <a name="syntax"></a>구문

```
__declspec( safebuffers )
```

## <a name="remarks"></a>설명

**/Gs** 컴파일러 옵션을 설정 하면 스택에 보안 검사를 삽입 하 여 컴파일러가 버퍼 오버런을 테스트 합니다. 보안 검사에 적합 한 데이터 구조 유형은 [/gs (버퍼 보안 검사)](../build/reference/gs-buffer-security-check.md)에 설명 되어 있습니다. 버퍼 오버런 검색에 대 한 자세한 내용은 [MSVC의 보안 기능](https://devblogs.microsoft.com/cppblog/security-features-in-microsoft-visual-c/)을 참조 하세요.

전문가 수동 코드 검토 또는 외부 분석이 함수가 버퍼 오버런으로부터 안전한지 확인할 수 있습니다. 이 경우 **`__declspec(safebuffers)`** 함수 선언에 키워드를 적용 하 여 함수에 대 한 보안 검사를 억제할 수 있습니다.

> [!CAUTION]
> 그러나 버퍼 보안 검사는 중요한 보안 보호를 제공하고 성능에 별다른 영향을 미치지 않으므로, 함수의 성능이 매우 중요하고 해당 함수의 안전성이 파악되는 드문 경우를 제외하고, 버퍼 보안 검사를 억제하지 않도록 권장합니다.

## <a name="inline-functions"></a>인라인 함수

*기본 함수* 는 [인라인](inline-functions-cpp.md) 키워드를 사용 하 여 *보조 함수의* 복사본을 삽입할 수 있습니다. 키워드를 **`__declspec(safebuffers)`** 함수에 적용 하는 경우 해당 함수에 대해 버퍼 오버런 검색이 억제 됩니다. 그러나 인라이닝은 다음과 같은 방법으로 키워드에 영향을 줍니다 **`__declspec(safebuffers)`** .

두 함수에 모두 **/gs** 컴파일러 옵션이 지정 되어 있지만 primary 함수는 키워드를 지정 한다고 가정 합니다 **`__declspec(safebuffers)`** . 보조 함수의 데이터 구조는 보안 검사를 가능하게 하기 때문에 이 함수는 보안 검사를 억제하지 않습니다. 이 경우 다음과 같습니다.

- 컴파일러 최적화에 관계 없이 컴파일러에서 해당 함수를 강제로 인라인 하도록 보조 함수에 [__forceinline](inline-functions-cpp.md) 키워드를 지정 합니다.

- 보조 함수는 보안 검사에 적합 하기 때문에 키워드가 지정 된 경우에도 보안 검사가 기본 함수에도 적용 됩니다 **`__declspec(safebuffers)`** .

## <a name="example"></a>예제

다음 코드에서는 키워드를 사용 하는 방법을 보여 줍니다 **`__declspec(safebuffers)`** .

```cpp
// compile with: /c /GS
typedef struct {
    int x[20];
} BUFFER;
static int checkBuffers() {
    BUFFER cb;
    // Use the buffer...
    return 0;
};
static __declspec(safebuffers)
    int noCheckBuffers() {
    BUFFER ncb;
    // Use the buffer...
    return 0;
}
int wmain() {
    checkBuffers();
    noCheckBuffers();
    return 0;
}
```

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[__declspec](../cpp/declspec.md)<br/>
[키워드](../cpp/keywords-cpp.md)<br/>
[inline, __inline, \__forceinline](inline-functions-cpp.md)<br/>
[strict_gs_check](../preprocessor/strict-gs-check.md)
