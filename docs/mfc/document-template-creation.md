---
description: '자세히 알아보기: 문서 템플릿 만들기'
title: 문서 템플릿 만들기
ms.date: 11/04/2016
helpviewer_keywords:
- document templates [MFC]
- constructors [MFC], document template
- document templates [MFC], creating
- MFC, document templates
- templates [MFC], document templates
ms.assetid: c87f1821-7cbf-442e-9690-f126ae7fb783
ms.openlocfilehash: 60f85cf0a1c16e1aaa6057160c5b986001e18d84
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330256"
---
# <a name="document-template-creation"></a>문서 템플릿 만들기

**파일** 메뉴에서 **새로** 만들기 또는 **열기** 명령에 대 한 응답으로 새 문서를 만들 때 문서 템플릿은 문서를 볼 수 있는 새 프레임 창도 만듭니다.

문서 템플릿 생성자는 템플릿을 만들 수 있는 문서, 창 및 뷰 형식을 지정 합니다. 이는 문서 템플릿 생성자에 전달 하는 인수에 의해 결정 됩니다. 다음 코드는 샘플 응용 프로그램에 대 한 [Cmultidoctemplate](reference/cmultidoctemplate-class.md) 을 만드는 방법을 보여 줍니다.

[!code-cpp[NVC_MFCDocView#7](codesnippet/cpp/document-template-creation_1.cpp)]

새 개체에 대 한 포인터는 `CMultiDocTemplate` [Adddoctemplate](reference/cwinapp-class.md#adddoctemplate)에 대 한 인수로 사용 됩니다. 생성자에 대 한 인수에는 `CMultiDocTemplate` 문서 형식의 메뉴 및 액셀러레이터와 연결 된 리소스 ID와 [RUNTIME_CLASS](reference/run-time-object-model-services.md#runtime_class) 매크로의 세 가지 사용이 포함 됩니다. `RUNTIME_CLASS` 이라는 c + + 클래스에 대 한 [CRuntimeClass](reference/cruntimeclass-structure.md) 개체를 인수로 반환 합니다. `CRuntimeClass`문서 템플릿 생성자에 전달 된 세 개체는 문서를 만드는 과정에서 지정 된 클래스의 새 개체를 만드는 데 필요한 정보를 제공 합니다. 이 예제에서는 `CScribDoc` 개체가 연결 된 개체를 만드는 문서 템플릿 생성을 보여 줍니다 `CScribView` . 뷰는 표준 MDI 자식 프레임 창에 의해 프레임으로 묶여 있습니다.

## <a name="see-also"></a>참고 항목

[문서 템플릿 및 문서/뷰 만들기 프로세스](document-templates-and-the-document-view-creation-process.md)<br/>
[문서/뷰 만들기](document-view-creation.md)<br/>
[MFC 개체 간 관계](relationships-among-mfc-objects.md)<br/>
[새 문서, 창 및 뷰 만들기](creating-new-documents-windows-and-views.md)
