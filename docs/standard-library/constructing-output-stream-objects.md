---
description: '자세한 정보: 출력 스트림 개체 생성'
title: 출력 스트림 개체 생성
ms.date: 11/04/2016
helpviewer_keywords:
- output stream objects
ms.assetid: 93c8eab6-610c-4f48-b76d-1d960cac7641
ms.openlocfilehash: e730e4cb675b216fa56b5624feb69fadcd61400a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97233645"
---
# <a name="constructing-output-stream-objects"></a>출력 스트림 개체 생성

미리 정의된 `cout`, `cerr` 또는 `clog` 개체를 사용하는 경우에만 출력 스트림을 생성할 필요가 없습니다. 다음에 대한 생성자를 사용해야 합니다.

- [출력 파일 스트림 생성자](#vclrfoutputfilestreamconstructorsanchor1)

- [출력 문자열 스트림 생성자](#vclrfoutputstringstreamconstructorsanchor2)

## <a name="output-file-stream-constructors"></a><a name="vclrfoutputfilestreamconstructorsanchor1"></a> 출력 파일 스트림 생성자

두 가지 방법 중 하나로 출력 파일 스트림을 생성할 수 있습니다.

- 기본 생성자를 사용한 다음 `open` 멤버 함수를 호출합니다.

   ```cpp
   ofstream myFile; // Static or on the stack
   myFile.open("filename");

   ofstream* pmyFile = new ofstream; // On the heap
   pmyFile->open("filename");
   ```

- 생성자 호출에서 파일 이름 및 모드 플래그를 지정합니다.

   ```cpp
   ofstream myFile("filename", ios_base::out);
   ```

## <a name="output-string-stream-constructors"></a><a name="vclrfoutputstringstreamconstructorsanchor2"></a>출력 문자열 스트림 생성자

출력 문자열 스트림을 생성하려면 다음과 같은 방식으로 `ostringstream`을 사용할 수 있습니다.

```cpp
using namespace std;
// ...
ostringstream myString;
myString << "this is a test" << ends;

string sp = myString.str(); // Obtain string
cout << sp << endl;
```

`ends` "조작자"는 문자열에 필요한 null 종결 문자를 추가합니다.

## <a name="see-also"></a>참고 항목

[출력 스트림](../standard-library/output-streams.md)
