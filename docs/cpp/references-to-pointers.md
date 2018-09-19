---
title: 포인터에 대 한 참조 | Microsoft Docs
ms.custom: ''
ms.date: 08/20/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- references, to pointers
ms.assetid: 4ce48b08-1511-4d2f-a31f-95f99eac0c70
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a93321eeb05f0e0448dca607177fcba6e89089a8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46107080"
---
# <a name="references-to-pointers"></a>포인터에 대한 참조

포인터에 대한 참조는 개체에 대한 참조와 거의 같은 방법으로 선언할 수 있습니다. 포인터에 대한 참조를 선언하면 일반 포인터처럼 사용되는 수정 가능한 값이 생성됩니다.

## <a name="example"></a>예제

다음 코드 샘플은 포인터에 대한 포인터 사용과 포인터에 대한 참조 사용 간의 차이점을 보여 줍니다.

`Add1` 및 `Add2` 함수는 동일한 방식으로 호출되지는 않지만 기능상 동일합니다. 차이점은 `Add1`에서는 이중 간접 참조를 사용하지만 `Add2`에서는 포인터에 대한 참조의 편리성을 사용한다는 점입니다.

```cpp
// references_to_pointers.cpp
// compile with: /EHsc

#include <iostream>
#include <string>

// C++ Standard Library namespace
using namespace std;

enum {
   sizeOfBuffer = 132
};

// Define a binary tree structure.
struct BTree {
   char  *szText;
   BTree *Left;
   BTree *Right;
};

// Define a pointer to the root of the tree.
BTree *btRoot = 0;

int Add1( BTree **Root, char *szToAdd );
int Add2( BTree*& Root, char *szToAdd );
void PrintTree( BTree* btRoot );

int main( int argc, char *argv[] ) {
   // Usage message
   if( argc < 2 ) {
      cerr << "Usage: Refptr [1 | 2]" << "\n";
      cerr << "\nwhere:\n";
      cerr << "1 uses double indirection\n";
      cerr << "2 uses a reference to a pointer.\n";
      cerr << "\nInput is from stdin.\n";
      return 1;
   }

   char *szBuf = new char[sizeOfBuffer];
   if (szBuf == NULL) {
      cerr << "Out of memory!\n";
      return -1;
   }

   // Read a text file from the standard input device and
   //  build a binary tree.
   while( !cin.eof() )
   {
      cin.get( szBuf, sizeOfBuffer, '\n' );
      cin.get();

      if ( strlen( szBuf ) ) {
         switch ( *argv[1] ) {
            // Method 1: Use double indirection.
            case '1':
               Add1( &btRoot, szBuf );
               break;
            // Method 2: Use reference to a pointer.
            case '2':
               Add2( btRoot, szBuf );
               break;
            default:
               cerr << "Illegal value '"
                  << *argv[1]
                  << "' supplied for add method.\n"
                     << "Choose 1 or 2.\n";
               return -1;
         }
      }
   }
   // Display the sorted list.
   PrintTree( btRoot );
}

// PrintTree: Display the binary tree in order.
void PrintTree( BTree* MybtRoot ) {
   // Traverse the left branch of the tree recursively.
   if ( btRoot->Left )
      PrintTree( btRoot->Left );

   // Print the current node.
   cout << btRoot->szText << "\n";

   // Traverse the right branch of the tree recursively.
   if ( btRoot->Right )
      PrintTree( btRoot->Right );
}

// Add1: Add a node to the binary tree.
//       Uses double indirection.
int Add1( BTree **Root, char *szToAdd ) {
   if ( (*Root) == 0 ) {
      (*Root) = new BTree;
      (*Root)->Left = 0;
      (*Root)->Right = 0;
      (*Root)->szText = new char[strlen( szToAdd ) + 1];
      strcpy_s((*Root)->szText, (strlen( szToAdd ) + 1), szToAdd );
      return 1;
   }
   else {
      if ( strcmp( (*Root)->szText, szToAdd ) > 0 )
         return Add1( &((*Root)->Left), szToAdd );
      else
         return Add1( &((*Root)->Right), szToAdd );
   }
}

// Add2: Add a node to the binary tree.
//       Uses reference to pointer
int Add2( BTree*& Root, char *szToAdd ) {
   if ( Root == 0 ) {
      Root = new BTree;
      Root->Left = 0;
      Root->Right = 0;
      Root->szText = new char[strlen( szToAdd ) + 1];
      strcpy_s( Root->szText, (strlen( szToAdd ) + 1), szToAdd );
      return 1;
   }
   else {
      if ( strcmp( Root->szText, szToAdd ) > 0 )
         return Add2( Root->Left, szToAdd );
      else
         return Add2( Root->Right, szToAdd );
   }
}
```

```Output
Usage: Refptr [1 | 2]

where:
1 uses double indirection
2 uses a reference to a pointer.

Input is from stdin.
```

## <a name="see-also"></a>참고자료

[참조](../cpp/references-cpp.md)