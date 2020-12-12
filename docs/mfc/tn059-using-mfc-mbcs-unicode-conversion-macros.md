---
description: '자세히 알아보기: TN059: MFC m b c s/유니코드 변환 매크로 사용'
title: 'TN059: MFC MBCS-Unicode 변환 매크로 사용'
ms.date: 11/04/2016
helpviewer_keywords:
- MFCANS32.DLL
- Unicode [MFC], conversion macros
- Unicode [MFC], OLE interfaces
- conversion macros [MFC]
- converting Unicode
- MBCS [MFC], conversion macros
- macros [MFC], MBCS conversion macros
- TN059
ms.assetid: a2aab748-94d0-4e2f-8447-3bd07112a705
ms.openlocfilehash: c1b767a8d90f2c788a15c9e880056206e7d1326a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97214769"
---
# <a name="tn059-using-mfc-mbcsunicode-conversion-macros"></a>TN059: MFC MBCS/유니코드 변환 매크로 사용

> [!NOTE]
> 다음 기술 노트는 온라인 설명서에 먼저 포함되어 있었으므로 업데이트되지 않았습니다. 따라서 일부 절차 및 항목은 만료되거나 올바르지 않을 수 있습니다. 최신 정보를 보려면 온라인 설명서 색인에서 관심 있는 항목을 검색하는 것이 좋습니다.

이 참고에서는 AFXPRIV.H에 정의 된 MBCS/Unicode 변환에 매크로를 사용 하는 방법에 대해 설명 합니다. 이러한 매크로는 응용 프로그램이 OLE API를 직접 처리 하거나 어떤 이유로 든 종종 유니코드와 MBCS 간에 변환 해야 하는 경우에 유용 합니다.

## <a name="overview"></a>개요

MFC 3.x에서는 OLE 인터페이스가 호출 될 때 특수 DLL (MFCANS32.DLL)을 사용 하 여 유니코드와 MBCS 사이를 자동으로 변환 합니다. 이 DLL은 ole 응용 프로그램을 OLE Api 및 인터페이스가 MBCS 인 것 처럼 쓸 수 있도록 허용 하는 거의 투명 한 계층입니다 (Macintosh는 제외). 이 계층은 편리 하 고 응용 프로그램을 Win16에서 Win32 (MFC, Microsoft Word, Microsoft Excel 및 VBA)로 신속 하 게 이식할 수 있는 반면에이 기술을 사용 하는 Microsoft 응용 프로그램 중 일부에 불과합니다. 때로는 상당한 성능 저하가 있었습니다. 이러한 이유로 MFC 4.x는이 DLL을 사용 하지 않고 유니코드 OLE 인터페이스와 직접 통신 합니다. 이렇게 하려면 OLE 인터페이스를 호출할 때 MFC에서 MBCS로 변환 해야 하며, OLE 인터페이스를 구현할 때 유니코드에서 MBCS로 변환 해야 하는 경우가 많습니다. 이를 효율적이 고 쉽게 처리 하기 위해 많은 매크로를 만들어 이러한 변환을 더 쉽게 수행할 수 있습니다.

이러한 매크로 집합을 만드는 가장 큰 장애물 중 하나는 메모리 할당입니다. 문자열을 현재 위치로 변환할 수 없으므로 변환 된 결과를 저장할 새 메모리를 할당 해야 합니다. 다음과 같은 코드를 사용 하 여이 작업을 수행할 수 있습니다.

```
// we want to convert an MBCS string in lpszA
int nLen = MultiByteToWideChar(CP_ACP,
    0,
    lpszA, -1,
    NULL,
    NULL);

LPWSTR lpszW = new WCHAR[nLen];
MultiByteToWideChar(CP_ACP,
    0,
    lpszA, -1,
    lpszW,
    nLen);

// use it to call OLE here
pI->SomeFunctionThatNeedsUnicode(lpszW);

// free the string
delete[] lpszW;
```

이 접근 방식은 여러 문제로 인 한 것입니다. 주요 문제는 작성, 테스트 및 디버그 하는 데 많은 코드를 작성 하는 것입니다. 간단한 함수 호출인 것은 이제 훨씬 더 복잡 합니다. 또한이 작업을 수행 하는 데는 상당한 런타임 오버 헤드가 있습니다. 메모리는 힙에 할당 되어야 하며 변환이 수행 될 때마다 해제 되어야 합니다. 마지막으로, 위의 코드는 `#ifdefs` 유니코드 및 Macintosh 빌드에 적절 하 게 추가 해야 합니다 (이 변환을 수행 하지 않아도 됨).

제공 된 솔루션은 다양 한 플랫폼 간의 차이를 나타내는 몇 가지 매크로를 만들고, 2) 효율적인 메모리 할당 체계를 사용 하 고, 3)을 기존 소스 코드에 쉽게 삽입할 수 있습니다. 다음은 정의 중 하나의 예입니다.

```
#define A2W(lpa) (\
((LPCSTR)lpa == NULL) NULL : (\
    _convert = (strnlen(lpa)+1),\
    AfxA2WHelper((LPWSTR) alloca(_convert*2),
    lpa,
    _convert)\)\)
```

위의 코드 대신이 매크로를 사용 하는 것이 훨씬 더 간단 합니다.

```
// use it to call OLE here
USES_CONVERSION;
pI->SomeFunctionThatNeedsUnicode(T2OLE(lpszA));
```

변환이 필요한 추가 호출이 있지만 매크로를 사용 하는 것은 간단 하 고 효과적입니다.

각 매크로의 구현은 _alloca () 함수를 사용 하 여 힙 대신 스택에 메모리를 할당 합니다. 스택에서 메모리를 할당 하는 것은 힙에서 메모리를 할당 하는 것 보다 훨씬 빠릅니다 .이 경우 함수가 종료 되 면 메모리가 자동으로 해제 됩니다. 또한 매크로는 `MultiByteToWideChar` (또는)를 두 번 이상 호출 하지 않습니다 `WideCharToMultiByte` . 이 작업은 필요한 것 보다 약간 더 많은 메모리를 할당 하 여 수행 됩니다. MBC는 최대 하나의 **wchar** 로 변환 되 고 각 **wchar** 에 대해 최대 2 개의 mbc 바이트를 갖게 됩니다. 필요한 경우를 제외 하 고 항상 변환을 처리 하기에 충분 한 두 번째 호출에서 변환 함수에 대 한 두 번째 호출을 피할 수 있습니다. 도우미 함수를 호출 하면 `AfxA2Whelper` 변환을 수행 하기 위해 수행 해야 하는 인수 푸시 수가 줄어듭니다 (이 경우 직접 호출한 경우 보다 작은 코드가 생성 됨 `MultiByteToWideChar` ).

매크로에 임시 길이를 저장할 수 있는 공간이 있도록 하려면 변환 매크로를 사용 하는 각 함수에서이를 수행 하는 _convert 라는 지역 변수를 선언 해야 합니다. 이 작업은 위의 예제에서 볼 수 있듯이 USES_CONVERSION 매크로를 호출 하 여 수행 합니다.

제네릭 변환 매크로와 OLE 관련 매크로가 모두 있습니다. 이러한 두 가지 매크로 집합에 대해서는 아래에서 설명 합니다. 모든 매크로는 AFXPRIV.H에 있습니다.

## <a name="generic-conversion-macros"></a>제네릭 변환 매크로

제네릭 변환 매크로는 기본 메커니즘을 형성 합니다. 이전 섹션인 A2W에 표시 된 매크로 예제와 구현은 이러한 "generic" 매크로 중 하나입니다. OLE와 관련이 없습니다. 일반 매크로 집합은 다음과 같습니다.

```
A2CW      (LPCSTR) -> (LPCWSTR)
A2W      (LPCSTR) -> (LPWSTR)
W2CA      (LPCWSTR) -> (LPCSTR)
W2A      (LPCWSTR) -> (LPSTR)
```

텍스트 변환 외에도 `TEXTMETRIC` ,, `DEVMODE` `BSTR` 및 OLE 할당 문자열을 변환 하는 매크로 및 도우미 함수도 있습니다. 이러한 매크로는이 논의의 범위를 벗어났습니다. AFXPRIV.H을 참조 하세요. 해당 매크로에 대 한 자세한 내용

## <a name="ole-conversion-macros"></a>OLE 변환 매크로

OLE 변환 매크로는 **OLESTR** 문자를 필요로 하는 함수를 처리 하기 위해 특별히 설계 되었습니다. OLE 헤더를 검사 하는 경우 **Lpcolestr** 및 **OLECHAR** 에 대 한 많은 참조가 표시 됩니다. 이러한 형식은 플랫폼에 한정 되지 않는 방식으로 OLE 인터페이스에 사용 되는 문자 유형을 참조 하는 데 사용 됩니다. **OLECHAR** 는 **`char`** Win16 및 Macintosh 플랫폼과 Win32의 **WCHAR** 에 매핑됩니다.

MFC 코드의 **#ifdef** 지시문 수를 최소한으로 유지 하기 위해 OLE 문자열이 관련 된 각 변환에 대 한 유사한 매크로가 있습니다. 가장 일반적으로 사용 되는 매크로는 다음과 같습니다.

```
T2COLE   (LPCTSTR) -> (LPCOLESTR)
T2OLE   (LPCTSTR) -> (LPOLESTR)
OLE2CT   (LPCOLESTR) -> (LPCTSTR)
OLE2T   (LPCOLESTR) -> (LPCSTR)
```

다시 TEXTMETRIC, DEVMODE, BSTR 및 OLE 할당 문자열을 수행 하기 위한 유사한 매크로가 있습니다. AFXPRIV.H를 참조 하세요. 자세한 내용은 H를 추가 하세요.

## <a name="other-considerations"></a>기타 고려 사항

루프에서 매크로를 사용 하지 마십시오. 예를 들어 다음과 같은 종류의 코드를 작성 하지 않으려고 합니다.

```cpp
void BadIterateCode(LPCTSTR lpsz)
{
    USES_CONVERSION;
    for (int ii = 0; ii <10000; ii++)
    pI->SomeMethod(ii, T2COLE(lpsz));

}
```

위의 코드는 문자열의 내용에 따라 스택에서 메가바이트의 메모리를 할당 하 게 될 수 있습니다 `lpsz` . 루프의 각 반복에 대해 문자열을 변환 하는 데 시간도 소요 됩니다. 대신 이러한 상수 변환을 루프 밖으로 이동 합니다.

```cpp
void MuchBetterIterateCode(LPCTSTR lpsz)
{
    USES_CONVERSION;
    LPCOLESTR lpszT = T2COLE(lpsz);

    for (int ii = 0; ii <10000; ii++)
    pI->SomeMethod(ii, lpszT);

}
```

문자열이 상수가 아니면 메서드 호출을 함수로 캡슐화 합니다. 이렇게 하면 매번 변환 버퍼를 해제할 수 있습니다. 예를 들어:

```cpp
void CallSomeMethod(int ii, LPCTSTR lpsz)
{
    USES_CONVERSION;
    pI->SomeMethod(ii, T2COLE(lpsz));

}

void MuchBetterIterateCode2(LPCTSTR* lpszArray)
{
    for (int ii = 0; ii <10000; ii++)
    CallSomeMethod(ii, lpszArray[ii]);

}
```

반환 값이 반환 되기 전에 데이터의 복사본을 생성 하는 것을 암시 하지 않는 한 매크로 중 하나의 결과를 반환 하지 않습니다. 예를 들어 다음 코드는 올바르지 않습니다.

```
LPTSTR BadConvert(ISomeInterface* pI)
{
    USES_CONVERSION;
    LPOLESTR lpsz = NULL;
    pI->GetFileName(&lpsz);

LPTSTR lpszT = OLE2T(lpsz);

    CoMemFree(lpsz);

return lpszT; // bad! returning alloca memory
}
```

위의 코드는 반환 값을 값을 복사 하는 값으로 변경 하 여 해결할 수 있습니다.

```
CString BetterConvert(ISomeInterface* pI)
{
    USES_CONVERSION;
    LPOLESTR lpsz = NULL;
    pI->GetFileName(&lpsz);

LPTSTR lpszT = OLE2T(lpsz);

    CoMemFree(lpsz);

return lpszT; // CString makes copy
}
```

매크로는 사용 하기 쉬우며 코드에 쉽게 삽입할 수 있습니다. 하지만 위의 주의 사항에 설명 된 것 처럼 사용 하는 경우 주의 해야 합니다.

## <a name="see-also"></a>참고 항목

[번호로 기술 참고 사항](../mfc/technical-notes-by-number.md)<br/>
[범주별 기술 참고 사항](../mfc/technical-notes-by-category.md)
