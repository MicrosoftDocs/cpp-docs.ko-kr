---
description: '자세한 정보: 예외: OLE 예외'
title: '예외: OLE 예외'
ms.date: 11/04/2016
helpviewer_keywords:
- OLE, exceptions
- OLE exceptions [MFC]
- exceptions [MFC], OLE
- exception handling [MFC], OLE
- OLE exceptions [MFC], classes for handling
ms.assetid: 2f8e0161-b94f-48bb-a5a2-6f644b192527
ms.openlocfilehash: da2a92d23dc7c11735c75482febea60916af289f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97290520"
---
# <a name="exceptions-ole-exceptions"></a>예외: OLE 예외

OLE에서 예외를 처리 하는 방법 및 기능은 다른 예외를 처리 하는 방법과 동일 합니다. 예외 처리에 대 한 자세한 내용은 [예외 및 오류 처리에 대 한 최신 c + + 모범 사례](../cpp/errors-and-exception-handling-modern-cpp.md)문서를 참조 하세요.

모든 예외 개체는 추상 기본 클래스에서 파생 됩니다 `CException` . MFC는 OLE 예외를 처리 하기 위한 두 가지 클래스를 제공 합니다.

- [Coleexception](reference/coleexception-class.md) 일반적인 OLE 예외 처리

- [Coledispatchexception](reference/coledispatchexception-class.md) OLE 디스패치 (자동화) 예외를 생성 하 고 처리 하는 데 유용 합니다.

이러한 두 클래스의 차이점은 제공 하는 정보의 양과 사용 되는 위치입니다. `COleException` 에는 예외에 대 한 OLE 상태 코드를 포함 하는 공용 데이터 멤버가 있습니다. `COleDispatchException` 다음을 포함 하 여 추가 정보를 제공 합니다.

- 응용 프로그램별 오류 코드

- 오류 설명 (예: "디스크가 꽉 참")

- 응용 프로그램에서 사용자에 대 한 추가 정보를 제공 하는 데 사용할 수 있는 도움말 컨텍스트입니다.

- 응용 프로그램 도움말 파일의 이름입니다.

- 예외를 생성 한 응용 프로그램의 이름입니다.

`COleDispatchException` Microsoft Visual Basic와 같은 제품에서 사용할 수 있도록 자세한 정보를 제공 합니다. 메시지 상자나 기타 알림에서 구두 오류 설명을 사용할 수 있습니다. 도움말 정보를 사용 하 여 사용자가 예외를 발생 시킨 조건에 응답할 수 있습니다.

두 개의 전역 함수는 두 개의 OLE 예외 클래스인 [AfxThrowOleException](reference/exception-processing.md#afxthrowoleexception) 및 [AfxThrowOleDispatchException](reference/exception-processing.md#afxthrowoledispatchexception)에 해당 합니다. 이를 사용 하 여 일반 OLE 예외 및 OLE 디스패치 예외를 각각 throw 합니다.

## <a name="see-also"></a>참고 항목

[예외 처리](exception-handling-in-mfc.md)
