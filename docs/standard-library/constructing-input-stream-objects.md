---
description: '자세한 정보: 입력 스트림 개체 생성'
title: 입력 스트림 개체 생성
ms.date: 11/04/2016
helpviewer_keywords:
- input stream objects
ms.assetid: ab94866e-6ffe-4f15-b4db-0bd23e636075
ms.openlocfilehash: 2ee1e0bb310c608b53a79afd101aaeafb3cb6645
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97324921"
---
# <a name="constructing-input-stream-objects"></a>입력 스트림 개체 생성

`cin` 개체만 사용하는 경우 입력 스트림을 생성할 필요가 없습니다. 다음을 사용하는 경우 입력 스트림을 생성해야 합니다.

- [입력 파일 스트림 생성자](#vclrfinputfilestreamconstructorsanchor8)

- [입력 문자열 스트림 생성자](#vclrfinputstringstreamconstructorsanchor9)

## <a name="input-file-stream-constructors"></a><a name="vclrfinputfilestreamconstructorsanchor8"></a>입력 파일 스트림 생성자

입력 파일 스트림을 만드는 방법에는 두 가지가 있습니다.

- **`void`** 인수 생성자를 사용한 다음 멤버 함수를 호출 합니다 `open` .

   ```cpp
   ifstream myFile; // On the stack
   myFile.open("filename");

   ifstream* pmyFile = new ifstream; // On the heap
   pmyFile->open("filename");
   ```

- 생성자 호출에서 파일 이름 및 모드 플래그를 지정합니다. 그렇게 하면 생성 프로세스 중 파일이 열립니다.

   ```cpp
   ifstream myFile("filename");
   ```

## <a name="input-string-stream-constructors"></a><a name="vclrfinputstringstreamconstructorsanchor9"></a>입력 문자열 스트림 생성자

입력 문자열 스트림 생성자를 사용하려면 미리 할당되고 미리 초기화된 스토리지의 주소가 필요합니다.

```cpp
string s("123.45");

double amt;
istringstream myString(s);

//istringstream myString("123.45") also works
myString>> amt; // amt contains 123.45
```

## <a name="see-also"></a>참고 항목

[입력 스트림](../standard-library/input-streams.md)
