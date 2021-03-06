---
title: Определения типов &lt;streambuf&gt;
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::streambuf
- iosfwd/std::wstreambuf
ms.assetid: 2678e18f-f0f0-4995-bc53-f1bc7dfc4ec6
ms.openlocfilehash: 1c9850ad7d7ec9b9c3554e6806f4790ef3613b08
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/16/2020
ms.locfileid: "79425067"
---
# <a name="ltstreambufgt-typedefs"></a>Определения типов &lt;streambuf&gt;

|||
|-|-|
|[streambuf](#streambuf)|[wstreambuf](#wstreambuf)|

## <a name="streambuf"></a>  streambuf

Специализация `basic_streambuf`, которая использует **char** в качестве параметров шаблона.

```cpp
typedef basic_streambuf<char, char_traits<char>> streambuf;
```

### <a name="remarks"></a>Remarks

Этот тип является синонимом для шаблона класса [basic_streambuf](../standard-library/basic-streambuf-class.md), специализированного для элементов типа **char** с признаками символа по умолчанию.

## <a name="wstreambuf"></a>  wstreambuf

Специализация `basic_streambuf`, которая использует **wchar_t** в качестве параметров шаблона.

```cpp
typedef basic_streambuf<wchar_t, char_traits<wchar_t>> wstreambuf;
```

### <a name="remarks"></a>Remarks

Этот тип является синонимом для шаблона класса [basic_streambuf](../standard-library/basic-streambuf-class.md), специализированного для элементов типа **wchar_t** с признаками символа по умолчанию.

## <a name="see-also"></a>См. также раздел

[\<streambuf>](../standard-library/streambuf.md)
