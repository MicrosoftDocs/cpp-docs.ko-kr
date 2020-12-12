---
description: '자세히 알아보기: 데이터 교환'
title: 데이터 교환
ms.date: 11/04/2016
helpviewer_keywords:
- property sheets [MFC], data exchange
- exchanging data with property sheets [MFC]
- DDX (dialog data exchange) [MFC], property sheets
ms.assetid: 689f02d0-51a9-455b-8ffb-5b44f0aefa28
ms.openlocfilehash: 9163434d51e3fa248f858434aece8f420e63197d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97290450"
---
# <a name="exchanging-data"></a>데이터 교환

대부분의 대화 상자와 마찬가지로 속성 시트와 응용 프로그램 간의 데이터 교환은 속성 시트의 가장 중요 한 기능 중 하나입니다. 이 문서에서는이 작업을 수행 하는 방법을 설명 합니다.

속성 시트를 사용 하 여 데이터를 교환 하는 것은 실제로 속성 시트의 개별 속성 페이지와 데이터를 교환 하는 것입니다. 속성 페이지를 사용 하 여 데이터를 교환 하는 절차는 [CPropertyPage](reference/cpropertypage-class.md) 개체가 특수 [CDialog](reference/cdialog-class.md) 개체 이기 때문에 대화 상자를 사용 하 여 데이터를 교환 하는 절차와 동일 합니다. 이 절차에서는 대화 상자의 컨트롤과 대화 상자 개체의 멤버 변수 간에 데이터를 교환 하는 프레임 워크의 DDX (대화 상자 데이터 교환) 기능을 활용 합니다.

속성 시트와 일반 대화 상자를 사용 하 여 데이터를 교환 하는 경우의 중요 한 차이점은 속성 시트에 여러 페이지가 있으므로 속성 시트의 모든 페이지와 데이터를 교환 해야 한다는 것입니다. DDX에 대 한 자세한 내용은 [대화 상자 데이터 교환 및 유효성 검사](dialog-data-exchange-and-validation.md)를 참조 하세요.

다음 예에서는 뷰와 속성 시트의 두 페이지 간에 데이터를 교환 하는 방법을 보여 줍니다.

[!code-cpp[NVC_MFCDocView#4](codesnippet/cpp/exchanging-data_1.cpp)]

## <a name="see-also"></a>참고 항목

[속성 시트](property-sheets-mfc.md)
