---
title: "&lt;filesystem&gt; 연산자 | Microsoft 문서"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- FILESYSTEM/std::experimental::filesystem::operator==
- FILESYSTEM/std::experimental::filesystem::operator!=
- FILESYSTEM/std::experimental::filesystem::operator<
- FILESYSTEM/std::experimental::filesystem::operator<=
- FILESYSTEM/std::experimental::filesystem::operator>
- FILESYSTEM/std::experimental::filesystem::operator>=
- FILESYSTEM/std::experimental::filesystem::operator/
- FILESYSTEM/std::experimental::filesystem::operator<<
- FILESYSTEM/std::experimental::filesystem::operator>>
dev_langs:
- C++
ms.assetid: 102c4833-aa3b-41a8-8998-f5003c546bfd
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2fea2837179018e703547a6a66d712404b19a28a
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/23/2018
---
# <a name="ltfilesystemgt-operators"></a>&lt;filesystem&gt; 연산자
연산자는 문자열로 두 경로의 어휘 비교를 수행합니다. **equivalent** 함수를 사용하여 두 경로(예: 상대 경로 및 절대 경로)가 디스크에서 동일한 파일 또는 디렉터리를 나타내는지 확인합니다.  
  
```  
C:\root> D:\root: false  
C:\root> C:\root\sub: false  
C:\root> C:\roo: true  
```  
  
 자세한 내용은 [파일 시스템 탐색(C++)](../standard-library/file-system-navigation.md)을 참조하세요.  
  
## <a name="operator"></a>operator==  
  
```  
bool operator==(const path& left, const path& right) noexcept;  
```  
  
 함수는 left.native() == right.native()를 반환합니다.  
  
## <a name="operator"></a>operator!=  
  
```  
bool operator!=(const path& left, const path& right) noexcept;  
```  
  
 함수는 !(left == right)를 반환합니다.  
  
## <a name="operator"></a>operator<  
  
```  
bool operator<(const path& left, const path& right) noexcept;  
```  
  
 함수는 left.native() < right.native()를 반환합니다.  
  
## <a name="operator"></a>operator<=  
  
```  
bool operator<=(const path& left, const path& right) noexcept;  
```  
  
 함수는 !(right \< left)를 반환합니다.  
  
## <a name="operator"></a>operator>  
  
```  
bool operator>(const path& left, const path& right) noexcept;  
```  
  
 함수는 right \< left를 반환합니다.  
  
## <a name="operator"></a>operator>=  
  
```  
bool operator>=(const path& left, const path& right) noexcept;  
```  
  
 함수는 !(left < right)를 반환합니다.  
  
## <a name="operator"></a>operator/  
  
```  
path operator/(const path& left, const path& right);
```  
  
 함수는 다음을 실행합니다.  
  
```  
basic_string<Elem, Traits> str;  
path ans = left;  
return (ans /= right);
```  
  
## <a name="operator"></a>operator<<  
  
```  
template <class Elem, class Traits>  
basic_ostream<Elem, Traits>& operator<<(basic_ostream<Elem, Traits>& os, const path& pval);
```  
  
 함수는 os << pval.string\<Elem, Traits>()를 반환합니다.  
  
## <a name="operator"></a>operator>>  
  
```  
template <class Elem, class Traits>  
basic_istream<Elem, Traits>& operator<<(basic_istream<Elem, Traits>& is, const path& pval);
```  
  
 함수는 다음을 실행합니다.  
  
```  
basic_string<Elem, Traits> str;  
is>> str;  
pval = str;  
return (is);
```  
  
## <a name="see-also"></a>참고 항목  
 [path 클래스(C++ 표준 라이브러리)](../standard-library/path-class.md)   
 [파일 시스템 탐색(C++)](../standard-library/file-system-navigation.md)   
 [\<filesystem>](../standard-library/filesystem.md)

