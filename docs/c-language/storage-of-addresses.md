---
title: "주소 저장소 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- storage [C++], addresses
- addresses [C++], storage of
ms.assetid: 423b2402-b847-4788-ad70-943b7c9c5c8b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bd82f6f5046cf910fbc871be37d4af5856796792
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="storage-of-addresses"></a>주소 저장소
주소에 필요한 저장소의 크기 및 주소의 의미는 컴파일러의 구현에 따라 다릅니다. 다른 형식에 대한 포인터가 동일한 길이가 되도록 보장되지 않습니다. 따라서 **sizeof(char \*)**가 **sizeof(int \*)**와 반드시 일치하는 것은 아닙니다.  
  
 **Microsoft 전용**  
  
 Microsoft C 컴파일러의 경우 **sizeof(char \*)**는 **sizeof(int \*)**와 일치합니다.  
  
 **Microsoft 전용 종료**  
  
## <a name="see-also"></a>참고 항목  
 [포인터 선언](../c-language/pointer-declarations.md)