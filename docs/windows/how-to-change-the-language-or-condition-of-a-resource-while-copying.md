---
title: '방법: 복사 하는 동안 언어 또는 리소스의 상태를 변경 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.resvw.resource.changing
dev_langs:
- C++
helpviewer_keywords:
- Language property
- condition property of resource
ms.assetid: 8f622ab0-bac2-468f-ae70-78911afc4759
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 508655dbfeb2d06d936d2b73d5435cf04c860f4b
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42598936"
---
# <a name="how-to-change-the-language-or-condition-of-a-resource-while-copying"></a>방법: 복사할 때 리소스의 언어 또는 조건 변경

리소스에서 복사하는 동안 언어 속성이나 조건 속성 또는 두 가지 모두를 변경할 수 있습니다.

- 리소스의 언어는 말 그대로 리소스용 언어를 식별합니다. 이 사용 됩니다 [FindResource](http://msdn.microsoft.com/library/windows/desktop/ms648042) 를 찾고 있는 리소스를 식별 하는 데 있습니다. (그러나 언어별로 리소스에 텍스트와 관련 없는 차이점이 있을 수 있습니다. 예를 들어 액셀러레이터가 일본어 자판에서만 작동하거나 비트맵이 중국어로 지역화된 빌드에서만 적절하게 작동하는 경우가 있을 수 있습니다.)

- 리소스의 조건은 리소스의 해당 특정 복사본이 사용되는 조건을 식별하는 정의된 기호입니다.

리소스의 언어와 조건은 작업 영역 창에서 리소스 이름 뒤에 오는 괄호 안에 표시됩니다. 이 예제에서는 IDD_AboutBox라는 리소스가 언어로 핀란드 어를 사용하며 조건이 XX33입니다.

```cpp
IDD_AboutBox (Finnish - XX33)  
```

### <a name="to-copy-an-existing-resource-and-change-its-language-or-condition"></a>기존 리소스를 복사하고 해당 언어 또는 조건을 변경하려면

1. .Rc 파일 또는 합니다 [리소스 뷰](../windows/resource-view-window.md) 창에서 복사 하려는 리소스를 마우스 오른쪽 단추로 클릭 합니다.

2. 선택할 **복사본 삽입** 바로 가기 메뉴에서.

3. 에 **리소스 복사본 삽입** 대화 상자:

   - 에 대 한 합니다 **언어** 목록 상자에서 언어를 선택 합니다.

   - 에 **조건을** 상자에서 조건을 입력 합니다.

## <a name="requirements"></a>요구 사항

Win32

## <a name="see-also"></a>참고 항목

[방법: 리소스 복사](../windows/how-to-copy-resources.md)  
[리소스 파일](../windows/resource-files-visual-studio.md)  
[리소스 편집기](../windows/resource-editors.md)