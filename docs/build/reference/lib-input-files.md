---
title: LIB 입력 파일
ms.date: 11/04/2016
f1_keywords:
- Lib
helpviewer_keywords:
- input files, LIB
ms.assetid: e1236f0d-cd90-446b-b900-f311f456085c
ms.openlocfilehash: fb0095bd9e8699fbc9a1a144833d12d2cf4a1f83
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57423094"
---
# <a name="lib-input-files"></a>LIB 입력 파일

LIB에서 예상한 입력된 파일 표에 표시 된 것 처럼가 사용 되 고 있는 모드에 따라 달라 집니다.

|모드|입력|
|----------|-----------|
|기본값 (빌드 또는 라이브러리를 수정 합니다.)|COFF 개체 (.obj) 파일, COFF 라이브러리 (.lib) 32 비트 개체 모델 형식 (OMF) 개체 (.obj) 파일|
|/EXTRACT을 사용 하 여 멤버 추출|COFF 라이브러리 (.lib)|
|내보내기 파일을 빌드하고 /def 라이브러리 가져오기|모듈 정의 (.def) 파일, COFF 개체 (.obj) 파일, COFF 라이브러리 (.lib), 32 비트 OMF 개체 (.obj) 파일|

> [!NOTE]
>  LIB 16 비트 버전에서 만들어진 OMF 라이브러리는 32 비트 버전의 LIB 입력으로 사용할 수 없습니다.

## <a name="see-also"></a>참고자료

[LIB 개요](../../build/reference/overview-of-lib.md)
