---
description: LIB 입력 파일에 대해 자세히 알아보세요.
title: LIB 입력 파일
ms.date: 11/04/2016
helpviewer_keywords:
- input files, LIB
ms.assetid: e1236f0d-cd90-446b-b900-f311f456085c
ms.openlocfilehash: f40cba91f0772e0073daca20a8f2093f3eec8aec
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97199547"
---
# <a name="lib-input-files"></a>LIB 입력 파일

LIB에서 필요한 입력 파일은 다음 표에 나와 있는 것 처럼 사용 되는 모드에 따라 달라 집니다.

|Mode|입력|
|----------|-----------|
|기본값 (라이브러리 작성 또는 수정)|COFF 개체 (.obj) 파일, COFF 라이브러리 (.lib), 32 비트 OMF (개체 모델 형식) 개체 (.obj) 파일|
|/EXTRACT를 사용 하 여 멤버 추출|COFF 라이브러리 (.lib)|
|/DEF를 사용 하 여 내보내기 파일 작성 및 라이브러리 가져오기|모듈 정의 (.def) 파일, COFF 개체 (.obj) 파일, COFF 라이브러리 (.lib), 32 비트 OMF 개체 (.obj) 파일|

> [!NOTE]
> 16 비트 버전의 LIB에서 만든 OMF 라이브러리는 32 비트 버전의 LIB에 대 한 입력으로 사용할 수 없습니다.

## <a name="see-also"></a>참고 항목

[LIB 개요](overview-of-lib.md)
