---
description: '자세한 정보: 컴파일러 오류 C2855'
title: 컴파일러 오류 C2855
ms.date: 02/16/2021
f1_keywords:
- C2855
helpviewer_keywords:
- C2855
ms.openlocfilehash: cc26dbf92ea385ee05681e5fab8b5c4257c2b525
ms.sourcegitcommit: e99db7c3b5f25ece0e152165066c926751a7c2ed
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/17/2021
ms.locfileid: "100643549"
---
# <a name="compiler-error-c2855"></a>컴파일러 오류 C2855

> '*option*' 명령줄 옵션이 미리 컴파일된 헤더와 일치 하지 않습니다.

이 오류는 명령줄 옵션이 미리 컴파일된 헤더를 만드는 데 사용 된 옵션과 다를 때 발생 합니다.

## <a name="remarks"></a>설명

컴파일러 옵션을 변경한 후 증분 빌드를 수행 하는 경우 오류 C2855 발생할 수 있습니다. 개별 소스 파일에 대 한 특정 컴파일러 옵션을 설정 하는 경우에도 발생할 수 있습니다.

이 오류를 해결 하려면 지정 된 명령줄 옵션을 사용 하 여 미리 컴파일된 헤더를 다시 생성 합니다. 미리 컴파일된 헤더를 다시 생성 하려면 연결 된 소스 파일을 작성 합니다. 예를 들어 Visual Studio 템플릿에서 만든 프로젝트는 일반적으로 라는 소스 파일을 만들어 *`pch.cpp`* 미리 컴파일된 헤더를 생성 합니다. 이전 버전의 Visual Studio에서이 파일의 이름은 *`stdafx.cpp`* 입니다. 다른 프로젝트에서 다시 빌드할 소스 파일은 [ `/Yc` (미리 컴파일된 헤더 파일 만들기)](../../build/reference/yc-create-precompiled-header-file.md) 컴파일러 옵션을 사용 하 여 빌드한 소스 파일입니다. 미리 컴파일된 헤더를 변경한 후 전체 프로젝트를 다시 빌드하는 것이 좋습니다.

## <a name="see-also"></a>참고 항목

[`/Y` (미리 컴파일된 헤더)](../../build/reference/y-precompiled-headers.md)\
[미리 컴파일된 헤더 파일](../../build/creating-precompiled-header-files.md)
