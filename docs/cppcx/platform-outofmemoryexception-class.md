---
title: "Platform:: outofmemoryexception 클래스 | Microsoft Docs"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::OutOfMemoryException
- VCCORLIB/Platform::OutOfMemoryException::OutOfMemoryException
dev_langs:
- C++
helpviewer_keywords:
- Platform::OutOfMemoryException
ms.assetid: 49c19f6b-f66c-4448-b861-91dcbf32de2c
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 609220fb92d936fcb400cabc0cca21b497e202f5
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2018
---
# <a name="platformoutofmemoryexception-class"></a>Platform::OutOfMemoryException 클래스
메모리가 부족하여 작업을 완료할 수 없는 경우 throw됩니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
public ref class OutOfMemoryException : COMException,    IException,    IPrintable,    IEquatable  
```  
  
### <a name="remarks"></a>설명  
 자세한 내용은 [COMException](../cppcx/platform-comexception-class.md) 클래스를 참조하세요.  
  
### <a name="requirements"></a>요구 사항  
 **지원 되는 최소 클라이언트:** Windows 8  
  
 **지원 되는 최소 서버:** Windows Server 2012  
  
 **네임스페이스:** Platform  
  
 **메타데이터:** platform.winmd  
  
## <a name="see-also"></a>참고 항목  
 [Platform::COMException 클래스](../cppcx/platform-comexception-class.md)