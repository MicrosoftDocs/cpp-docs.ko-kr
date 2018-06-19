---
title: 문자열 및 문자 리터럴 (c + +) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- R
dev_langs:
- C++
helpviewer_keywords:
- L constant
- escape sequences
- Null strings, null-terminated strings
- literal strings, C++
- Null strings
- string literals, syntax
- string literals
- literal strings
- strings [C++], string literals
- NULL, character constant
- wide characters, strings
ms.assetid: 61de8f6f-2714-4e7b-86b6-a3f885d3b9df
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cede3ee6efb063141fc9ba7db58c6ec1dbcae845
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32424604"
---
# <a name="string-and-character-literals--c"></a>문자열 및 문자 리터럴 (c + +)
C++를 사용하면 다양한 문자열 및 문자 형식이 지원되며 이러한 각 형식의 리터럴 값을 표현할 수 있습니다. 소스 코드에서는 문자 집합을 사용하여 문자 및 문자열 리터럴의 내용을 표현합니다. 유니버설 문자 이름 및 이스케이프 문자를 사용하면 기본 소스 문자 집합만 사용하여 모든 문자열을 표현할 수 있습니다. 원시 문자열 리터럴을 사용하면 이스케이프 문자를 사용하지 않아도 되며 원시 문자열 리터럴을 사용하여 모든 유형의 문자열 리터럴을 표현할 수 있습니다. 또한 추가 생성이나 변환 단계를 수행하지 않고도 std:: string 리터럴을 만들 수 있습니다.  
  
```cpp  
#include <string>  
using namespace std::string_literals; // enables s-suffix for std::string literals  
  
int main()  
{  
    // Character literals  
    auto c0 =   'A'; // char  
    auto c1 = u8'A'; // char  
    auto c2 =  L'A'; // wchar_t  
    auto c3 =  u'A'; // char16_t  
    auto c4 =  U'A'; // char32_t  
  
    // String literals  
    auto s0 =   "hello"; // const char*  
    auto s1 = u8"hello"; // const char*, encoded as UTF-8  
    auto s2 =  L"hello"; // const wchar_t*  
    auto s3 =  u"hello"; // const char16_t*, encoded as UTF-16  
    auto s4 =  U"hello"; // const char32_t*, encoded as UTF-32  
  
    // Raw string literals containing unescaped \ and "  
    auto R0 =   R"("Hello \ world")"; // const char*  
    auto R1 = u8R"("Hello \ world")"; // const char*, encoded as UTF-8  
    auto R2 =  LR"("Hello \ world")"; // const wchar_t*  
    auto R3 =  uR"("Hello \ world")"; // const char16_t*, encoded as UTF-16  
    auto R4 =  UR"("Hello \ world")"; // const char32_t*, encoded as UTF-32  
  
    // Combining string literals with standard s-suffix  
    auto S0 =   "hello"s; // std::string  
    auto S1 = u8"hello"s; // std::string  
    auto S2 =  L"hello"s; // std::wstring  
    auto S3 =  u"hello"s; // std::u16string  
    auto S4 =  U"hello"s; // std::u32string  
  
    // Combining raw string literals with standard s-suffix  
    auto S5 =   R"("Hello \ world")"s; // std::string from a raw const char*  
    auto S6 = u8R"("Hello \ world")"s; // std::string from a raw const char*, encoded as UTF-8  
    auto S7 =  LR"("Hello \ world")"s; // std::wstring from a raw const wchar_t*  
    auto S8 =  uR"("Hello \ world")"s; // std::u16string from a raw const char16_t*, encoded as UTF-16  
    auto S9 =  UR"("Hello \ world")"s; // std::u32string from a raw const char32_t*, encoded as UTF-32  
}  
```  
  
 문자열 리터럴에는 접두사가 없거나, 각각 좁은 문자(싱글바이트 또는 멀티바이트), UTF-8, 와이드 문자(UCS-2 또는 UTF-16), UTF-16 및 UTF-32 인코딩을 나타내는 `u8`, `L`, `u`및  `U` 접두사가 있습니다. 원시 문자열 리터럴에는 이러한 인코딩의 원시 버전에 해당하는 `R`, `u8R`, `LR`, `uR` 및 `UR` 접두사가 있을 수 있습니다.  임시 또는 정적 std:: string 값을 만들려면 `s` 접미사와 함께 문자열 리터럴이나 원시 문자열 리터럴을 사용할 수 있습니다. 자세한 내용은 아래의 문자열 리터럴 단원을 참조하세요. 기본 소스 문자에 대 한 자세한 내용은 집합, 유니버설 문자 이름 및 확장 된 코드 페이지에서 문자를 사용 하 여 소스 코드에서 참조 [문자 집합](../cpp/character-sets.md)합니다.  
  
## <a name="character-literals"></a>문자 리터럴  
 *문자 리터럴* 은 상수 문자로 구성됩니다. 문자 리터럴은 작은따옴표로 묶인 문자로 표현됩니다. 문자 리터럴의 5 가지 종류가 있습니다.  
  
-   유형의 일반 문자 리터럴 `char`예 `'a'`  
  
-   형식의 utf-8 문자 리터럴 `char`예 `u8'a'`  
  
-   `wchar_t`형식의 와이드 문자 리터럴(예: `L'a'`)  
  
-   형식의 utf-16 문자 리터럴 `char16_t`예 `u'a'`  
  
-   형식이 u t F-32 문자 리터럴 `char32_t`예 `U'a'`  
  
 문자 리터럴에 사용 되는 문자를 예약 된 문자 백슬래시를 제외한 모든 문자일 수 있습니다 ('\\'), 작은따옴표 (') 또는 줄 바꿈 합니다. 예약된 문자는 이스케이프 시퀀스를 사용하여 지정할 수 있습니다. 문자는 형식이 문자를 저장할 수 있을 만큼 큰 경우 유니버설 문자 이름을 사용하여 지정할 수 있습니다.  
  
### <a name="encoding"></a>인코딩  
 문자 리터럴 다르게 인코딩 되는 접두사를 기반으로 합니다.  
  
-   접두사가 없는 리터럴 문자는 일반 문자 리터럴. 일반 문자 리터럴 값에 이스케이프 시퀀스를 단일 문자가 포함 된 또는 실행 문자 집합에 나타낼 수 있는 유니버설 문자 이름에 실행 문자 집합에서 인코딩을의 숫자 값에는 값입니다. 일반 문자 리터럴 1 자, 이스케이프 시퀀스 또는 유니버설 문자 이름을 포함 하는 한 *일부일 리터럴*합니다. 여러 문자 리터럴 또는 실행 문자 집합으로 표현할 수 없는 일반 문자 리터럴의 조건부로-지원 되는 형식은 int 있으며 해당 값은 구현 시 정의 합니다.  
  
-   L 접두사로 시작 하는 문자 리터럴을 와이드 문자 리터럴입니다. 단일 문자, 이스케이프 시퀀스 또는 유니버설 문자 이름이 포함 된 와이드 문자 리터럴 값에서 문자 리터럴은 나타나지에 없는 경우 설정 실행 와이드 문자 인코딩을의 숫자 값에는 값에는 실행 와이드 문자는 있으며이 경우 값은 구현 시 정의에서 설정 합니다. 여러 문자, 이스케이프 시퀀스 또는 유니버설 문자 이름이 포함 된 와이드 문자 리터럴 값은 구현 시 정의 됩니다.  
  
-   U8 접두사로 시작 하는 문자 리터럴을 utf-8 문자 리터럴. Utf-8 문자 리터럴 값에 이스케이프 시퀀스를 단일 문자가 포함 된 또는 (C0 컨트롤 및 기본 라틴에 해당 하는 단일 u t F-8 코드 단위도 나타낼 수 있는 유니버설 문자 이름에 해당 ISO 10646 코드 포인트 값에는 값 유니코드 블록)입니다. 단일에 u t F-8 코드 단위 값을 표현할 수 없는 경우 프로그램 형식이 잘못 되었습니다. U t F-8 문자 리터럴에 둘 이상의 문자, 이스케이프 시퀀스 또는 유니버설 문자 이름이 포함 된 형식이 잘못 되었습니다.  
  
-   U 접두사로 시작 하는 문자 리터럴을 utf-16 문자 리터럴. (해당 하는 기본적인 다국어 평면에 단일 utf-16 코드 단위 나타낼 수 있는 유니버설 문자 이름에 해당 ISO 10646 코드 포인트 값에는 값 또는 utf-16 문자 리터럴 값에 이스케이프 시퀀스를 단일 문자가 포함 된 ). 값에 단일 utf-16 코드 단위 표현할 수 없는 경우 프로그램 형식이 잘못 되었습니다. U t F-16 문자 리터럴에 둘 이상의 문자, 이스케이프 시퀀스 또는 유니버설 문자 이름이 포함 된 형식이 잘못 되었습니다.  
  
-   U 접두사로 시작 하는 문자 리터럴을 u t F-32 문자 리터럴. U t F-32 문자 리터럴 값에 이스케이프 시퀀스를 단일 문자가 포함 된 또는 유니버설 문자 이름에 해당 ISO 10646 코드 포인트 값에는 값입니다. U t F-8 문자 리터럴에 둘 이상의 문자, 이스케이프 시퀀스 또는 유니버설 문자 이름이 포함 된 형식이 잘못 되었습니다.  
  
###  <a name="bkmk_Escape"></a> 이스케이프 시퀀스  
 이스케이프 시퀀스는 단순, 8진수 및 16진수의 세 종류가 있습니다. 이스케이프 시퀀스의 종류는 다음과 같습니다.  
  
|값|이스케이프 시퀀스|값|이스케이프 시퀀스|  
|-----------|---------------------|-----------|---------------------|  
|줄 바꿈|\n|백슬래시|\\\|  
|가로 탭|\t|물음표|? 또는 \\?|  
|세로 탭|\v|작은따옴표|\\'|  
|백스페이스|\b|큰따옴표|\\"|  
|캐리지 리턴|\r|null 문자|\0|  
|폼 피드|\f|8진수|\ooo|  
|경고(벨)|\a|16진수|\xhhh|  
  
 다음 코드는 일반 문자 리터럴을 사용 하는 이스케이프 문자의 예를 보여줍니다. 동일한 이스케이프 시퀀스 구문은 다른 문자 리터럴 형식에 유효 합니다.  
  
```cpp  
#include <iostream>  
using namespace std;  
  
int main() {  
    char newline = '\n';  
    char tab = '\t';  
    char backspace = '\b';  
    char backslash = '\\';  
    char nullChar = '\0';  
  
    cout << "Newline character: " << newline << "ending" << endl; // Newline character:  
                                                                  //  ending  
    cout << "Tab character: " << tab << "ending" << endl; // Tab character : ending  
    cout << "Backspace character: " << backspace << "ending" << endl; // Backspace character : ending  
    cout << "Backslash character: " << backslash << "ending" << endl; // Backslash character : \ending  
    cout << "Null character: " << nullChar << "ending" << endl; //Null character:  ending  
}  
```  
  
 **Microsoft 전용**  
  
 (접두사 없이 하)의 일반 문자 리터럴 값을 만들려면 컴파일러에는 문자 또는 문자 시퀀스는 32 비트 정수 내의 8 비트 값에 작은따옴표 사이의 변환 합니다. 리터럴의 여러 문자는 필요에 따라 상위에서 하위로 해당 바이트를 채웁니다. `char` 값을 만들기 위해 컴파일러는 하위 바이트를 사용합니다. `wchar_t` 또는 `char16_t` 값을 만들기 위해 컴파일러는 하위 단어를 사용합니다. 컴파일러는 비트가 할당된 바이트 또는 단어 이상으로 설정된 경우 결과가 잘린다고 경고합니다.  
  
```cpp  
char c0    = 'abcd';    // C4305, C4309, truncates to 'd'  
wchar_t w0 = 'abcd';    // C4305, C4309, truncates to '\x6364'  
```  
  
 8진수 이스케이프 시퀀스는 백슬래시와 그 뒤에 오는 최대 3자리의 8진수 문자열 시퀀스입니다. 4자리 이상의 숫자를 포함하는 것처럼 보이는 8진수 이스케이프 시퀀스의 동작은 3자리의 8진수 시퀀스로 처리되고 그다음에 후속 숫자를 문자로 처리하여 놀라운 결과를 제공할 수 있습니다. 예를 들어:  
  
```cpp  
char c1 = '\100';   // '@'  
char c2 = '\1000';  // C4305, C4309, truncates to '0'   
```  
  
 8진수가 아닌 문자를 포함하는 것처럼 보이는 이스케이프 시퀀스는 마지막 8진수 문자까지 8진수 시퀀스로 평가되고 그다음에 나머지 문자로 평가됩니다. 예를 들어:  
  
```cpp  
char c3 = '\009';   // '9'  
char c4 = '\089';   // C4305, C4309, truncates to '9'  
char c5 = '\qrs';   // C4129, C4305, C4309, truncates to 's'  
```  
  
 16진수 이스케이프 시퀀스는 백슬래시, 문자 `x`, 일련의 16진수 숫자의 순서로 구성됩니다. 16진수 숫자가 포함되지 않은 이스케이프 시퀀스는 컴파일러 오류 C2153: "16진 리터럴에는 16진수가 적어도 하나는 있어야 합니다."라는 오류를 발생합니다. 앞에 오는 0은 무시됩니다. 16진수 및 16진수가 아닌 문자를 포함하는 것처럼 보이는 이스케이프 시퀀스는 마지막 16진수 문자까지 16진수 이스케이프 시퀀스로 평가되고 그다음에 16진수가 아닌 문자로 평가됩니다.   일반 접두사가 없거나 u8 문자 리터럴에서 가장 큰 16 진수 값은 0xFF입니다. L 접두사 또는 u 접두사가 있는 와이드 문자 리터럴에서 가장 큰 16진수 값은 0xFFFF입니다. U 접두사가 있는 와이드 문자 리터럴에서 가장 큰 16진수 값은 0xFFFFFFFF입니다.  
  
```cpp  
char c6 = '\x0050'; // 'P'  
char c7 = '\x0pqr'; // C4305, C4309, truncates to 'r'  
```  
  
 `L` 접두사가 있는 와이드 문자 리터럴에 둘 이상의 문자가 포함된 경우 값은 첫 번째 문자에서 가져옵니다. 후속 문자는 해당 하는 일반 문자 리터럴의 동작과 달리 무시 됩니다.  
  
```cpp  
wchar_t w1 = L'\100';   // L'@'  
wchar_t w2 = L'\1000';  // C4066 L'@', 0 ignored   
wchar_t w3 = L'\009';   // C4066 L'\0', 9 ignored  
wchar_t w4 = L'\089';   // C4066 L'\0', 89 ignored  
wchar_t w5 = L'\qrs';   // C4129, C4066 L'q' escape, rs ignored  
wchar_t w6 = L'\x0050'; // L'P'  
wchar_t w7 = L'\x0pqr'; // C4066 L'\0', pqr ignored  
```  
  
 **Microsoft 전용 종료**  
  
 백슬래시 문자 (\\)는 줄 연속 문자가 줄의 끝에 배치 됩니다. 백슬래시 문자가 문자 리터럴로 표시되도록 하려면 두 개의 백슬래시(`\\`)를 연속하여 입력해야 합니다. 줄 연속 문자에 대한 자세한 내용은 [Phases of Translation](../preprocessor/phases-of-translation.md)를 참조하세요.  
  
###  <a name="bkmk_UCN"></a> 유니버설 문자 이름  
 문자 리터럴 및 네이티브(비 원시) 문자열 리터럴에서는 유니버설 문자 이름으로 모든 문자를 나타낼 수 있습니다.  유니버설 문자 이름은 접두사 \U와 그다음에 오는 8자리 숫자 유니코드 코드 포인트 또는 접두사 \u와 그다음에 오는 4자리 숫자 유니코드 코드 포인트로 구성됩니다. 올바른 형식의 유니버설 문자 이름을 만들려면 모든 8자리 또는 4자리 숫자가 각각 있어야 합니다.  
  
```cpp  
char u1 = 'A';          // 'A'  
char u2 = '\101';       // octal, 'A'   
char u3 = '\x41';       // hexadecimal, 'A'  
char u4 = '\u0041';     // \u UCN 'A'  
char u5 = '\U00000041'; // \U UCN 'A'  
```  
  
 **서로게이트 쌍**  
  
 유니버설 문자 이름은 서로게이트 코드 포인트 범위 D800-DFFF의 값을 인코딩할 수 없습니다. 유니코드 서로게이트 쌍에 대해 `\UNNNNNNNN`을 사용하여 유니버설 문자 이름을 지정합니다. 여기서 NNNNNNNN은 문자에 대한 8자리 코드 포인트입니다. 컴파일러는 필요한 경우 서로게이트 쌍을 생성합니다.  
  
 C++03에서는 해당 유니버설 문자 이름을 사용해서만 문자 하위 집합을 나타낼 수 있으며 실제로 유효한 유니코드 문자를 나타내지 않는 일부 유니버설 문자 이름이 허용됩니다. C++11 표준에서 이것이 수정되었습니다. C++11에서는 문자 및 문자열 리터럴과 식별자 모두 유니버설 문자 이름을 사용할 수 있습니다.  유니버설 문자 이름에 대 한 자세한 내용은 참조 하십시오. [문자 집합](../cpp/character-sets.md)합니다. 유니코드에 대한 자세한 내용은 [유니코드](http://msdn.microsoft.com/library/dd374081\(v=vs.85\).aspx)(영문)를 참조하세요. 서로게이트 쌍에 대한 자세한 내용은 [서로게이트 쌍 및 보조 문자](http://msdn.microsoft.com/library/dd374069\(v=vs.85\).aspx)(영문)를 참조하세요.  
  
## <a name="string-literals"></a>문자열 리터럴  
 문자열 리터럴은 함께 사용되어 null로 끝나는 문자열을 형성하는 문자 시퀀스를 나타냅니다. 문자를 큰따옴표로 묶어야 합니다. 다음과 같은 종류의 문자열 리터럴이 있습니다.  
  
### <a name="narrow-string-literals"></a>좁은 문자열 리터럴  
 좁은 문자열 리터럴에 접두사가 없고 큰따옴표로 구분 된 null로 끝나는 배열 형식의 `const char[n]`여기서 n은 바이트에서 배열의 길이입니다. 좁은 문자열 리터럴에는 큰따옴표(`"`), 백슬래시(`\`) 또는 줄 바꿈 문자를 제외한 모든 그래픽 문자가 포함될 수 있습니다. 또한 좁은 문자열 리터럴에는 위에 나열된 이스케이프 시퀀스 및 바이트 크기에 맞는 유니버설 문자 이름이 포함될 수 있습니다.  
  
```cpp  
const char *narrow = "abcd";  
  
// represents the string: yes\no  
const char *escaped = "yes\\no";  
```  
  
#### <a name="utf-8-encoded-strings"></a>UTF-8로 인코딩된 문자열  
  
 U t F-8로 인코딩된 문자열은는 u8 접두사가 큰따옴표로 구분 된 null로 끝나는 배열 형식의 `const char[n]`, 여기서 n은 인코딩된 바이트 배열 길이입니다. u8 접두사가 있는 문자열 리터럴에는 큰따옴표(`"`), 백슬래시(`\`) 또는 줄 바꿈 문자를 제외한 모든 그래픽 문자가 포함될 수 있습니다. 또한 u8 접두사가 있는 문자열 리터럴에는 위에 나열된 이스케이프 시퀀스 및 모든 유니버설 문자 이름이 포함될 수 있습니다.  
  
```cpp  
const char* str1 = u8"Hello World";  
const char* str2 = u8"\U0001F607 is O:-)";  
```  
  
### <a name="wide-string-literals"></a>와이드 문자열 리터럴  
 와이드 문자열 리터럴에 상수의 null로 끝나는 배열 `wchar_t` 이 붙 '`L`' 큰따옴표 ("), 백슬래시를 제외한 모든 그래픽 문자를 포함 하 고 (\\), 또는 줄 바꿈 문자입니다. 와이드 문자열 리터럴에는 위에 나열된 이스케이프 시퀀스 및 모든 유니버설 문자 이름이 포함될 수 있습니다.  
  
```cpp  
const wchar_t* wide = L"zyxw";  
const wchar_t* newline = L"hello\ngoodbye";  
```  
  
#### <a name="char16t-and-char32t-c11"></a>char16_t 및 char32_t(C++11)  
  
 C++11에서는 이식 가능한 `char16_t` (16비트 유니코드) 및 `char32_t` (32비트 유니코드) 문자 형식이 도입되었습니다.  
  
```cpp  
auto s3 = u"hello"; // const char16_t*  
auto s4 = U"hello"; // const char32_t*  
```  
  
### <a name="raw-string-literals-c11"></a>원시 문자열 리터럴(C++11)  
 원시 문자열 리터럴은 null로 끝나는 배열-모든 문자 형식의-큰따옴표 ("), 백슬래시를 포함 하 여 모든 그래픽 문자를 포함 하는 (\\), 또는 줄 바꿈 문자입니다. 원시 문자열 리터럴은 문자 클래스를 사용하는 정규식과 HTML 문자열 및 XML 문자열에 종종 사용됩니다. 예제를 보려면 다음 문서를 참조: [Bjarne Stroustrup의 C + + 11 FAQ](http://go.microsoft.com/fwlink/p/?linkid=401172)합니다.  
  
```cpp  
// represents the string: An unescaped \ character  
const char* raw_narrow = R"(An unescaped \ character)";  
const wchar_t* raw_wide = LR"(An unescaped \ character)";  
const char*       raw_utf8  = u8R"(An unescaped \ character)";  
const char16_t* raw_utf16 = uR"(An unescaped \ character)";  
const char32_t* raw_utf32 = UR"(An unescaped \ character)";  
```  
  
 구분 기호는 원시 문자열 리터럴의 여는 괄호 바로 앞에 오고 닫는 괄호 바로 뒤에 오는 최대 16자의 사용자 정의 시퀀스입니다.  예를 들어 `R"abc(Hello"\()abc"` 에서 구분 기호 시퀀스는 `abc` 이고 문자열 콘텐츠는 `Hello"\(`입니다. 구분 기호를 사용하여 큰따옴표와 괄호를 모두 포함하는 원시 문자열을 구분할 수 있습니다. 이러한 문자열을 사용하면 컴파일러 오류가 발생합니다.  
  
```cpp  
// meant to represent the string: )"  
const char* bad_parens = R"()")";  // error C2059  
```  
  
 그러나 구분 기호를 사용하면 오류가 해결됩니다.  
  
```cpp  
const char* good_parens = R"xyz()")xyz";  
```  
  
 다음과 같이 소스에 줄 바꿈 문자(이스케이프된 문자가 아님)가 있는 원시 문자열 리터럴을 생성할 수 있습니다.  
  
```cpp  
// represents the string: hello  
//goodbye  
const wchar_t* newline = LR"(hello  
goodbye)";  
```  
  
### <a name="stdstring-literals-c14"></a>std::string 리터럴(C++14)  
 std::string 리터럴은 "xyx"(접미사 `s` 사용)로 표현되는 사용자 정의 리터럴(아래 참조)의 표준 라이브러리 구현입니다. 이 종류의 문자열 리터럴은 지정된 접두사에 따라 std::string, std::wstring, std::u32string 또는 std::u16string 형식의 임시 개체를 생성합니다. 위와 같이 접두사를 사용하지 않으면 std::string이 생성됩니다. L"xyz"는 std::wstring을 생성합니다. u"xyz"는 [std::u16string](../standard-library/string-typedefs.md#u16string)을 생성하고, U"xyz"는 [std::u32string](../standard-library/string-typedefs.md#u32string)을 생성합니다.  
  
```cpp  
//#include <string>  
//using namespace std::string_literals;  
string str{ "hello"s };  
string str2{ u8"Hello World" };  
wstring str3{ L"hello"s };  
u16string str4{ u"hello"s };  
u32string str5{ U"hello"s };  
```  
  
 접미사 s는 원시 문자열 리터럴에도 사용할 수 있습니다.  
  
```cpp  
u32string str6{ UR"(She said "hello.")"s };  
```  
  
 네임 스페이스에 정의 된 std:: string 리터럴은 `std::literals::string_literals` 에 \<문자열 > 헤더 파일입니다. `std::literals::string_literals`및 `std::literals` 가 모두 [인라인 네임스페이스](../cpp/namespaces-cpp.md)로 선언되기 때문에 `std::literals::string_literals` 는 자동으로 네임스페이스 `std`에 직접 속한 것처럼 처리됩니다.  
  
### <a name="size-of-string-literals"></a>문자열 리터럴의 크기  
 ANSI char\* 문자열 및 다른 싱글바이트 인코딩 (utf-8 아님), 리터럴 문자열의 바이트 단위로 크기는 null 종결 문자에 대 한 1 문자 수입니다. 다른 모든 문자열 형식의 경우, 리터럴 크기는 문자 수와 엄밀하게 관련이 있지는 않습니다. UTF-8에서는 최대 네 개의 문자 요소를 사용하여 일부 *코드 단위*를 인코드하고, UTF-16으로 인코드된 char16_t 또는 wchar_t에서는 총 4바이트에 대해 두 개의 요소를 사용하여 단일 *코드 단위*를 인코드할 수 있습니다.   이 예제에서는 와이드 문자열 리터럴의 크기(바이트)를 보여 줍니다.  
  
```cpp  
const wchar_t* str = L"Hello!";  
const size_t byteSize = (wcslen(str) + 1) * sizeof(wchar_t);  
```  
  
 다음에 유의 `strlen()` 및 `wcslen()` null 종결 문자를 필요에 따라 크기가 문자열 형식의 요소 크기와 같은지의 크기를 포함 하지 않습니다: char * 문자열에서 1 바이트, wchar_t에 2 바이트\* 또는 char16_t\* 문자열 및 char32_t의 경우 4 바이트\* 문자열입니다.  
  
 문자열 리터럴의 최대 길이는 65535바이트입니다. 이 제한은 좁은 문자열 리터럴과 와이드 문자열 리터럴 모두에 적용됩니다.  
  
### <a name="modifying-string-literals"></a>문자열 리터럴 수정  
 문자열 리터럴은 상수이므로(std:string 리터럴을 제외), 이를 수정하려고 하면(예: str[2] = 'A') 컴파일러 오류가 발생합니다.  
  
 **Microsoft 전용**  
  
 Visual C++에서는 문자열 리터럴을 사용하여 포인터를 비상수 `char` 또는 `wchar_t`로 초기화할 수 있습니다. 이는 C99 코드에서 허용되지만 C++98에서는 더 이상 사용되지 않으며 C++11에서는 제거되었습니다. 문자열을 수정하려고 하면 다음 예제와 같이 액세스 위반이 발생합니다.  
  
```cpp  
wchar_t* str = L"hello";  
str[2] = L'a'; // run-time error: access violation  
```  
  
 설정할 때 문자열 리터럴이 non_const 문자 포인터로 변환 될 때 오류를 내보내도록 컴파일러에 발생할 수 있습니다는 [/zc: strictstrings (문자열 리터럴 형식 변환 사용 안 함)](../build/reference/zc-strictstrings-disable-string-literal-type-conversion.md) 컴파일러 옵션입니다. 표준 규격의 이식 가능한 코드에 권장됩니다. 또한 `auto` 키워드는 올바른 (const) 형식으로 확인되기 때문에 이를 사용하여 문자열 리터럴 초기화 포인터를 선언하는 것이 좋습니다. 예를 들어 다음 코드 예제는 컴파일 시간에 문자열 리터럴에 쓰려는 시도를 catch합니다.  
  
```cpp  
auto str = L"hello";  
str[2] = L'a'; // C3892: you cannot assign to a variable that is const.  
```  
  
 경우에 따라 실행 파일의 공간을 절약하기 위해 동일한 문자열 리터럴이 풀링될 수 있습니다. 문자열 리터럴 풀링에서 컴파일러는 각 참조가 문자열 리터럴의 별도 인스턴스를 가리키는 것이 아니라 특정 문자열 리터럴에 대한 모든 참조가 메모리의 같은 위치를 가리키게 합니다. 문자열 풀링을 사용하려면 [/GF](../build/reference/gf-eliminate-duplicate-strings.md) 컴파일러 옵션을 사용하세요.  
  
 **End Microsoft Specific**  
  
### <a name="concatenating-adjacent-string-literals"></a>인접 문자열 리터럴 연결  
 인접하는 와이드 문자열 리터럴 또는 좁은 문자열 리터럴은 연결됩니다. 다음 선언은  
  
```cpp  
char str[] = "12" "34";  
```  
  
 다음 선언과 동일합니다.  
  
```cpp  
char atr[] = "1234";  
```  
  
 또한 다음 선언과 동일합니다.  
  
```cpp  
char atr[] =  "12\  
34";  
```  
  
 포함된 16진수 이스케이프 코드를 사용하여 문자열 리터럴을 지정하면 예기치 않은 결과가 발생할 수 있습니다. 다음 예제는 ASCII 5 문자와 f, i, v 및 e 문자가 포함된 문자열 리터럴을 만들려고 합니다.  
  
```cpp  
"\x05five"  
```  
  
 실제 결과는 16진수 5F(ASCII 코드의 밑줄)와 i, v 및 e 문자입니다. 올바른 결과를 얻으려면 다음 중 하나를 사용합니다.  
  
```cpp  
"\005five"     // Use octal literal.  
"\x05" "five"  // Use string splicing.  
```  
  
 std::string 리터럴은 std::string 형식이므로 [basic_string](../standard-library/basic-string-class.md) 형식에 대해 정의된 + 연산자를 사용하여 연결할 수 있습니다. 또한 인접 문자열 리터럴과 동일한 방식으로 연결할 수도 있습니다. 두 경우 모두, 문자열 인코딩과 접미사가 다음과 일치해야 합니다.  
  
```cpp  
auto x1 = "hello" " " " world"; // OK  
auto x2 = U"hello" " " L"world"; // C2308: disagree on prefix  
auto x3 = u8"hello" " "s u8"world"s; // OK, agree on prefixes and suffixes  
auto x4 = u8"hello" " "s u8"world"z; // C3688, disagree on suffixes  
```  
  
### <a name="string-literals-with-universal-character-names"></a>유니버설 문자 이름을 가진 문자열 리터럴  
 네이티브(비 원시) 문자열 리터럴은 문자열 형식에서 하나 이상의 문자로 유니버설 문자 이름을 인코드할 수 있는 한 유니버설 문자 이름을 사용하여 모든 문자를 나타낼 수 있습니다.  예를 들어 확장된 문자를 나타내는 유니버설 문자 이름은 ANSI 코드 페이지를 사용하는 좁은 문자열로 인코드할 수 없지만 일부 멀티바이트 코드 페이지의 좁은 문자열, UTF-8 문자열 또는 와이드 문자열로 인코드할 수 있습니다. C + + 11에서는 유니코드 지원이 char16_t * 및 char32_t으로 확장 됩니다\* 문자열 형식:  
  
```cpp  
// ASCII smiling face  
const char*     s1 = ":-)";    
  
// UTF-16 (on Windows) encoded WINKING FACE (U+1F609)  
const wchar_t*  s2 = L"😉 = \U0001F609 is ;-)";    
  
// UTF-8  encoded SMILING FACE WITH HALO (U+1F607)  
const char*     s3 = u8"😇 = \U0001F607 is O:-)";  
  
// UTF-16 encoded SMILING FACE WITH OPEN MOUTH (U+1F603)  
const char16_t* s4 = u"😃 = \U0001F603 is :-D";  
  
// UTF-32 encoded SMILING FACE WITH SUNGLASSES (U+1F60E)  
const char32_t* s5 = U"😎 = \U0001F60E is B-)";  
```  
  
## <a name="see-also"></a>참고 항목  
 [문자 집합](../cpp/character-sets.md)   
 [숫자, 부울 및 포인터 리터럴](../cpp/numeric-boolean-and-pointer-literals-cpp.md)   
 [사용자 정의 리터럴](../cpp/user-defined-literals-cpp.md)