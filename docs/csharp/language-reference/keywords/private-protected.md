---
title: "私有受保护 （C# 参考）"
ms.date: 11/15/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
author: sputier
ms.author: wiwagn
ms.openlocfilehash: 5f7abd2569d5bad5af64161042e4e5d21e741c8c
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/18/2017
---
# <a name="private-protected-c-reference"></a>私有受保护 （C# 参考）
`private protected`这个关键字组合是一个成员访问修饰符。用此修饰符修饰的成员，只能被派生自该成员所在类、并且在同一个程序集的class所使用(相同于CLR的family and assembly)。 有关 `private protected` 和其他访问修饰符的比较，请参阅[可访问性级别](../../../csharp/language-reference/keywords/accessibility-levels.md)。 
   
## <a name="example"></a>示例  
 变量的静态类型是派生的类类型，基类的私有受保护的成员才可从其包含的程序集中的派生类型访问。 以下面的代码段为例：  
  
 ```
 // Assembly1.cs  
 // Compile with: /target:library  
 public class BaseClass
 {
     private protected int myValue = 0;
 }
 
 public class DerivedClass1 : BaseClass
 {
     void Access()
     {
         BaseClass baseObject = new BaseClass();
 
         // Error CS1540, because myValue can only be accessed by
         // classes derived from BaseClass.
         // baseObject.myValue = 5;  
 
         // OK, accessed through the current derived class instance
         myValue = 5;
     }
 }
```  
  
```  
 // Assembly2.cs  
 // Compile with: /reference:Assembly1.dll  
 class DerivedClass2 : BaseClass
 {
     void Access()
     {
         // Error CS0122, because myValue can only be
         // accessed by types in Assembly1
         // myValue = 10;
     }
 }
```  
 此示例包含两个文件，即 `Assembly1.cs` 和 `Assembly2.cs`。 第一个文件包含公共的基类， `BaseClass`，和由它派生的类型`DerivedClass1`。 `BaseClass`拥有专用的受保护的成员， `myValue`，后者`DerivedClass1`尝试以两种方式访问。 首次尝试访问`myValue`的实例通过`BaseClass`将产生错误。 但是，尝试将其用作中继承的成员`DerivedClass1`将会成功。
在第二个文件中，尝试访问`myValue`的继承的成员作为`DerivedClass2`将产生错误，因为仅由派生类型中 Assembly1 访问它。 

 结构成员不能为`private protected`由于结构不能被继承。  
  
## <a name="c-language-specification"></a>C# 语言规范  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>请参阅  
 [C# 参考](../../../csharp/language-reference/index.md)   
 [C# 编程指南](../../../csharp/programming-guide/index.md)   
 [C# 关键字](../../../csharp/language-reference/keywords/index.md)   
 [访问修饰符](../../../csharp/language-reference/keywords/access-modifiers.md)   
 [可访问性级别](../../../csharp/language-reference/keywords/accessibility-levels.md)   
 [修饰符](../../../csharp/language-reference/keywords/modifiers.md)   
 [public](../../../csharp/language-reference/keywords/public.md)   
 [private](../../../csharp/language-reference/keywords/private.md)   
 [internal](../../../csharp/language-reference/keywords/internal.md)   
 [Internal virtual 关键字的安全问题](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))
