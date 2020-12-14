---
description: 다음에 대 한 자세한 정보:/TLS
title: /TLS
ms.date: 11/04/2016
f1_keywords:
- /TLS
helpviewer_keywords:
- /TLS dumpbin option
- -TLS dumpbin option
ms.assetid: 2b3f48f9-cac4-4351-b15c-2833b43bc709
ms.openlocfilehash: a21ef03210a65bb50899ba3907911272ac52b0db
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97229953"
---
# <a name="tls"></a>/TLS

실행 파일의 IMAGE_TLS_DIRECTORY 구조를 표시 합니다.

## <a name="remarks"></a>설명

/TLS는 tls의 필드 및 TLS 콜백 함수의 주소를 표시 합니다.

프로그램에서 스레드 로컬 저장소를 사용 하지 않는 경우 해당 이미지에는 TLS 구조가 포함 되지 않습니다.  자세한 내용은 [스레드](../../cpp/thread.md) 를 참조 하세요.

IMAGE_TLS_DIRECTORY는 winnt.exe에 정의 되어 있습니다.

## <a name="see-also"></a>참고 항목

[DUMPBIN 옵션](dumpbin-options.md)
