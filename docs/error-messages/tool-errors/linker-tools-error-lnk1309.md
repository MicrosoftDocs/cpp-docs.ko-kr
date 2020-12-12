---
description: '자세한 정보: 링커 도구 오류 LNK1309'
title: 링커 도구 오류 LNK1309
ms.date: 11/04/2016
f1_keywords:
- LNK1309
helpviewer_keywords:
- LNK1309
ms.assetid: 10146071-883f-4849-97d1-c7468f90efbb
ms.openlocfilehash: e04498ae5226f748b6ba5cc2ce0cd9340f4547c2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97193645"
---
# <a name="linker-tools-error-lnk1309"></a>링커 도구 오류 LNK1309

> *type1* 모듈이 검색 되었습니다. 잘못 된 with switch/CLRIMAGETYPE:*type2*

## <a name="remarks"></a>설명

**/CLRIMAGETYPE** 를 사용 하 여 CLR 이미지 형식을 요청 했지만, 하나 이상의 모듈이 해당 형식과 호환 되지 않기 때문에 링커가 해당 형식의 이미지를 생성할 수 없습니다.

예를 들어 **/CLRIMAGETYPE: safe** 를 지정 하 고 **/clr: pure** 로 빌드된 모듈을 전달 하는 경우 LNK1309이 표시 됩니다.

**/Clr: pure** 및 **/clr: safe** 컴파일러 옵션 및 지원 라이브러리는 visual studio 2015에서 더 이상 사용 되지 않으며 visual studio 2017에서는 지원 되지 않습니다.

Ptrustu [d] .lib를 사용 하 여 부분적으로 신뢰할 수 있는 CLR 순수 응용 프로그램을 빌드하려고 하는 경우 LNK1309도 표시 됩니다. 부분적으로 신뢰할 수 있는 응용 프로그램을 만드는 방법에 대 한 자세한 내용은 [방법: CRT 라이브러리 DLL에 대 한 종속성을 제거 하 여 부분적으로 신뢰할 수 있는 응용 프로그램 만들기](../../dotnet/create-a-partially-trusted-application.md)를 참조 하세요.

자세한 내용은 [/clr (공용 언어 런타임 컴파일)](../../build/reference/clr-common-language-runtime-compilation.md) 및 [/CLRIMAGETYPE (Clr 이미지 형식 지정)](../../build/reference/clrimagetype-specify-type-of-clr-image.md)를 참조 하세요.
