---
title: "如何：对实现 GridView 的 ListView 中的项进行分组"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ListView controls [WPF], grouping items with GridViews
- grouping items in ListViews implementing GridViews [WPF]
- GridView controls [WPF], grouping items
ms.assetid: eebef25b-ddc6-424e-a66d-ea228d1bf33d
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8a97a6c85036a6daf4e8c908186953f9a75f952a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-group-items-in-a-listview-that-implements-a-gridview"></a>如何：对实现 GridView 的 ListView 中的项进行分组
此示例演示如何显示组中的项数<xref:System.Windows.Controls.GridView>的查看模式<xref:System.Windows.Controls.ListView>控件。  
  
## <a name="example"></a>示例  
 用于显示组中的项数<xref:System.Windows.Controls.ListView>，定义<xref:System.Windows.Data.CollectionViewSource>。 下面的示例演示<xref:System.Windows.Data.CollectionViewSource>数据项根据的值进行分组`Catalog`数据字段。  
  
 [!code-xaml[GridViewWithGroups#GroupingCollectionViewSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#groupingcollectionviewsource)]  
  
 下面的示例设置<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>为<xref:System.Windows.Controls.ListView>到<xref:System.Windows.Data.CollectionViewSource>前面的示例定义。 该示例还定义<xref:System.Windows.Controls.ItemsControl.GroupStyle%2A>实现<xref:System.Windows.Controls.Expander>控件。  
  
 [!code-xaml[GridViewWithGroups#ListViewGroups](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#listviewgroups)]  
[!code-xaml[GridViewWithGroups#ListViewEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#listviewend)]  
  
## <a name="see-also"></a>请参阅  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [帮助主题](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [ListView 概述](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [GridView 概述](../../../../docs/framework/wpf/controls/gridview-overview.md)
