---
title: Generic Procedures in Visual Basic
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- generic methods [Visual Basic], type inference
- generics [Visual Basic], type inference
- procedures [Visual Basic], generic
- generic procedures
- type inference, generics
- generic methods [Visual Basic]
- type inference
- generics [Visual Basic], procedures
- generic procedures [Visual Basic], type inference
ms.assetid: 95577b28-137f-4d5c-a149-919c828600e5
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e019ca32277f93f798e99e996a3670c8302ba9b9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/21/2017
---
# <a name="generic-procedures-in-visual-basic"></a>Generic Procedures in Visual Basic
A*泛型过程*，也称为*泛型方法*，是使用至少一个类型参数定义的过程。 这使得能够根据其需求的数据类型调整调用该过程每次调用代码。  
  
 过程不是泛型是简单地由于正在在泛型类或泛型结构内定义的。 若要为泛型，该过程必须采用至少一个类型参数，除了可能需要的任何普通参数。 泛型类或结构可以包含非泛型过程和非泛型类、 结构或模块可以包含泛型过程。  
  
 泛型过程可以使用其类型参数在其普通参数列表中，如果它具有一个，并在其过程的代码是与其返回类型。  
  
## <a name="type-inference"></a>类型推断  
 未提供任何类型自变量在所有情况下，可以调用泛型过程。 如果它调用这种方式，编译器将尝试确定要将传递给过程的类型参数的相应数据类型。 这称为*类型推理*。 下面的代码演示一个调用中，编译器推断，它应通过类型`String`给类型参数`t`。  
  
 [!code-vb[VbVbalrDataTypes#15](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_1.vb)]  
  
 如果编译器无法推断调用上下文中的类型参数，则将报告错误。 此类错误的一个可能的原因是数组的秩不匹配。 例如，假设你定义普通参数作为类型参数的数组。 如果调用的泛型过程提供的不同秩 （维数），数组不匹配会导致类型推理失败。 下面的代码演示一个调用中的一个二维数组传递给期望一维数组的过程。  
  
 `Public Sub demoSub(Of t)(ByVal arg() As t)`  
  
 `End Sub`  
  
 `Public Sub callDemoSub()`  
  
 `Dim twoDimensions(,) As Integer`  
  
 `demoSub(twoDimensions)`  
  
 `End Sub`  
  
 你可以调用仅通过省略所有类型自变量的类型推理。 如果你提供一个类型自变量，你必须提供所有这些值。  
  
 仅为泛型过程支持的类型推理。 不能调用上泛型类、 结构、 接口或委托的类型推理。  
  
## <a name="example"></a>示例  
  
### <a name="description"></a>描述  
 下面的示例定义了一个泛型`Function`过程，用于在一个数组中查找特定元素。 它定义一个类型参数，并使用它来构建在参数列表中的两个参数。  
  
### <a name="code"></a>代码  
 [!code-vb[VbVbalrDataTypes#14](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_2.vb)]  
  
### <a name="comments"></a>注释  
 前面的示例中需要此功能用于比较`searchValue`针对的每个元素`searchArray`。 若要确保此功能，它可以约束类型参数`T`实现<xref:System.IComparable%601>接口。 该代码使用<xref:System.IComparable%601.CompareTo%2A>方法而不是`=`运算符，因为没有为提供一个类型自变量不能保证`T`支持`=`运算符。  
  
 你可以测试`findElement`过程替换为以下代码。  
  
 [!code-vb[VbVbalrDataTypes#13](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_3.vb)]  
  
 前面调用`MsgBox`分别显示"0"、"1"和"-1"。  
  
## <a name="see-also"></a>另请参阅  
 [Visual Basic 中的泛型类型](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [如何：定义可对不同数据类型提供相同功能的类](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)  
 [如何：使用泛型类](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [过程](../../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [过程参数和自变量](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)  
 [类型列表](../../../../visual-basic/language-reference/statements/type-list.md)  
 [参数列表](../../../../visual-basic/language-reference/statements/parameter-list.md)
