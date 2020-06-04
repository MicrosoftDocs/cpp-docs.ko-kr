---
title: '방법: 등록이 필요 없는 COM 구성 요소 빌드'
ms.date: 11/04/2016
helpviewer_keywords:
- COM components, registration-free
ms.assetid: 7e585d6a-0314-45b2-8f1b-cae9ac4df037
ms.openlocfilehash: 783677c97835acc98751fc4a19f9405af752b71a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62188940"
---
# <a name="how-to-build-registration-free-com-components"></a>방법: 등록이 필요 없는 COM 구성 요소 빌드

등록이 필요 없는 COM 구성 요소는 DLL에 기본 제공된 매니페스트가 있는 COM 구성 요소입니다.

### <a name="to-build-manifests-into-com-components"></a>COM 구성 요소에 매니페스트를 빌드하려면

1. COM 구성 요소의 프로젝트 속성 페이지를 엽니다.

1. **구성 속성** 노드를 확장한 다음 **매니페스트 도구** 노드를 확장합니다.

1. **입력 및 출력** 속성 페이지를 선택한 후 **매니페스트 포함** 속성을 **예**로 설정합니다.

1. **확인**을 클릭합니다.

1. 솔루션을 빌드합니다.

## <a name="see-also"></a>참조

[방법: COM 구성 요소를 사용하는 격리된 애플리케이션 빌드](how-to-build-isolated-applications-to-consume-com-components.md)
