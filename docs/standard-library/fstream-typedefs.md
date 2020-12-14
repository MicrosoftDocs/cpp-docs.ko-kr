---
description: '자세한 정보: &lt; a m &gt; 형식 정의'
title: '&lt;fstream&gt; 형식 정의'
ms.date: 11/04/2016
f1_keywords:
- fstream/std::filebuf
- fstream/std::fstream
- fstream/std::ifstream
- fstream/std::ofstream
- fstream/std::wfilebuf
- fstream/std::wfstream
- fstream/std::wifstream
- fstream/std::wofstream
ms.assetid: 8dddef2d-7f17-42a6-ba08-6f6f20597d23
ms.openlocfilehash: cf3a7d686bb1e6d6004aaf91fa50294225f0362d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97232254"
---
# <a name="ltfstreamgt-typedefs"></a>&lt;fstream&gt; 형식 정의

[filebuf](#filebuf)\
[a m](#fstream)\
[ifstream](#ifstream)\
[ofstream](#ofstream)\
[wfilebuf](#wfilebuf)\
[wfstream](#wfstream)\
[wifstream](#wifstream)\
[wofstream](#wofstream)

## <a name="filebuf"></a><a name="filebuf"></a> filebuf

`basic_filebuf`템플릿 매개 변수에서 특수화 된 형식 **`char`** 입니다.

```cpp
typedef basic_filebuf<char, char_traits<char>> filebuf;
```

### <a name="remarks"></a>설명

이 형식은 [](../standard-library/basic-filebuf-class.md) **`char`** 기본 문자 특성을 포함 하는 형식의 요소에 대해 특수화 된 클래스 템플릿 basic_filebuf의 동의어입니다.

## <a name="fstream"></a><a name="fstream"></a> a m

`basic_fstream`템플릿 매개 변수에서 특수화 된 형식 **`char`** 입니다.

```cpp
typedef basic_fstream<char, char_traits<char>> fstream;
```

### <a name="remarks"></a>설명

이 형식은 [](../standard-library/basic-fstream-class.md) **`char`** 기본 문자 특성을 포함 하는 형식의 요소에 대해 특수화 된 클래스 템플릿 basic_fstream의 동의어입니다.

## <a name="ifstream"></a><a name="ifstream"></a> ifstream

파일에서 직렬로 싱글바이트 문자 데이터를 읽는 데 사용할 스트림을 정의합니다. `ifstream` 는의 클래스 템플릿을 특수화 하는 typedef `basic_ifstream` 입니다 **`char`** .

`wifstream` `basic_ifstream` 더블 와이드 문자를 읽도록 특수화 된 typedef도 있습니다 **`wchar_t`** . 자세한 내용은 [wifstream](../standard-library/fstream-typedefs.md#wifstream)을 참조하세요.

```cpp
typedef basic_ifstream<char, char_traits<char>> ifstream;
```

### <a name="remarks"></a>설명

이 형식은 기본 문자 특성을 포함 하는 char 형식의 요소에 대해 특수화 된 클래스 템플릿 [basic_ifstream](../standard-library/basic-ifstream-class.md)의 동의어입니다. 예제는 다음과 같습니다.

```cpp
using namespace std;

ifstream infile("existingtextfile.txt");

if (!infile.bad())
{
    // Dump the contents of the file to cout.
    cout << infile.rdbuf();infile.close();
}
```

## <a name="ofstream"></a><a name="ofstream"></a> ofstream

`basic_ofstream`템플릿 매개 변수에서 특수화 된 형식 **`char`** 입니다.

```cpp
typedef basic_ofstream<char, char_traits<char>> ofstream;
```

### <a name="remarks"></a>설명

이 형식은 [](../standard-library/basic-ofstream-class.md) **`char`** 기본 문자 특성을 포함 하는 형식의 요소에 대해 특수화 된 클래스 템플릿 basic_ofstream의 동의어입니다.

## <a name="wfstream"></a><a name="wfstream"></a> wfstream

`basic_fstream`템플릿 매개 변수에서 특수화 된 형식 **`wchar_t`** 입니다.

```cpp
typedef basic_fstream<wchar_t, char_traits<wchar_t>> wfstream;
```

### <a name="remarks"></a>설명

이 형식은 [](../standard-library/basic-fstream-class.md) **`wchar_t`** 기본 문자 특성을 포함 하는 형식의 요소에 대해 특수화 된 클래스 템플릿 basic_fstream의 동의어입니다.

## <a name="wifstream"></a><a name="wifstream"></a> wifstream

`basic_ifstream`템플릿 매개 변수에서 특수화 된 형식 **`wchar_t`** 입니다.

```cpp
typedef basic_ifstream<wchar_t, char_traits<wchar_t>> wifstream;
```

### <a name="remarks"></a>설명

이 형식은 [](../standard-library/basic-ifstream-class.md) **`wchar_t`** 기본 문자 특성을 포함 하는 형식의 요소에 대해 특수화 된 클래스 템플릿 basic_ifstream의 동의어입니다.

## <a name="wofstream"></a><a name="wofstream"></a> wofstream

`basic_ofstream`템플릿 매개 변수에서 특수화 된 형식 **`wchar_t`** 입니다.

```cpp
typedef basic_ofstream<wchar_t, char_traits<wchar_t>> wofstream;
```

### <a name="remarks"></a>설명

이 형식은 [](../standard-library/basic-ofstream-class.md) **`wchar_t`** 기본 문자 특성을 포함 하는 형식의 요소에 대해 특수화 된 클래스 템플릿 basic_ofstream의 동의어입니다.

## <a name="wfilebuf"></a><a name="wfilebuf"></a> wfilebuf

`basic_filebuf`템플릿 매개 변수에서 특수화 된 형식 **`wchar_t`** 입니다.

```cpp
typedef basic_filebuf<wchar_t, char_traits<wchar_t>> wfilebuf;
```

### <a name="remarks"></a>설명

이 형식은 [](../standard-library/basic-filebuf-class.md) **`wchar_t`** 기본 문자 특성을 포함 하는 형식의 요소에 대해 특수화 된 클래스 템플릿 basic_filebuf의 동의어입니다.

## <a name="see-also"></a>참고 항목

[\<fstream>](../standard-library/fstream.md)
