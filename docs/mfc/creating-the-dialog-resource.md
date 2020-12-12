---
description: '자세히 알아보기: 대화 상자 리소스 만들기'
title: 대화 상자 리소스 만들기
ms.date: 11/04/2016
helpviewer_keywords:
- dialog resources
- MFC dialog boxes [MFC], creating
- dialog templates [MFC], creating dialog resource
- templates [MFC], creating
- resources [MFC], creating dialog boxes
- MFC dialog boxes [MFC], dialog resource
ms.assetid: 0b83bd33-14d3-4611-8129-fccdae18053e
ms.openlocfilehash: 999a63d11981b8d21be85096ff49813c92b15810
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97309721"
---
# <a name="creating-the-dialog-resource"></a>대화 상자 리소스 만들기

대화 상자를 디자인 하 고 대화 [상자](dialog-boxes.md) 리소스를 만들려면 대화 상자 [편집기](../windows/dialog-editor.md)를 사용 합니다. 대화 상자 편집기에서는 다음을 수행할 수 있습니다.

- 대화 상자가 나타날 때 대화 상자의 크기 및 위치를 조정합니다.

- 컨트롤 팔레트에서 여러 종류의 컨트롤을 끌어서 대화 상자에서 원하는 위치에 놓습니다.

- 도구 모음에서 맞춤 단추를 사용하여 컨트롤을 배치합니다.

- 프로그램에서 대화 상자에 지정할 모양 및 동작을 시뮬레이션하여 대화 상자를 테스트합니다. 테스트 모드에서는 텍스트 상자에 텍스트를 입력하고, 입력 단추를 클릭하는 등 대화 상자의 컨트롤을 조작할 수 있습니다.

작업을 마치면 대화 상자 템플릿 리소스가 애플리케이션의 리소스 스크립트 파일에 저장됩니다. 필요한 경우 나중에 편집할 수 있습니다. 대화 상자 리소스를 만들고 편집 하는 방법에 대 한 전체 설명은 [대화 상자 편집기](../windows/dialog-editor.md) 항목을 참조 하세요. 이 기법은 [CFormView](reference/cformview-class.md) 및 [CRecordView](reference/crecordview-class.md) 클래스에 대 한 대화 상자 템플릿 리소스를 만드는 데에도 사용 됩니다.

대화 상자의 모양이 사용자에 게 적합 한 경우 대화 상자 클래스를 만들고 [코드 마법사를 사용 하 여 대화 상자 클래스 만들기](creating-a-dialog-class-with-code-wizards.md)에 설명 된 대로 메시지를 매핑합니다.

## <a name="see-also"></a>참고 항목

[대화 상자](dialog-boxes.md)<br/>
[MFC에서 대화 상자를 통해 작업](life-cycle-of-a-dialog-box.md)
