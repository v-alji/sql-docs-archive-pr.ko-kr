---
title: 이름 열에 특성 바인딩 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- binding attributes [Analysis Services]
- name columns [Analysis Services]
- attributes [Analysis Services], binding
ms.assetid: 467f0cf3-8691-476d-a7fb-a5df4e374eaf
author: minewiskan
ms.author: owend
ms.openlocfilehash: e25c59d34744e7a067c2b3e83d248c4674772737
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660181"
---
# <a name="bind-an-attribute-to-a-name-column"></a><span data-ttu-id="85d50-102">이름 열로 특성 바인딩</span><span class="sxs-lookup"><span data-stu-id="85d50-102">Bind an Attribute to a Name Column</span></span>
  <span data-ttu-id="85d50-103">이 절차에서는 차원 디자이너의 **특성** 창과 **개체 바인딩** 대화 상자를 사용하여 수동으로 이름 열에 특성을 바인딩하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="85d50-103">This procedure describes how to bind an attribute to a name column manually by using the **Attributes** pane in the Dimension Designer and by using the **Object Binding** dialog box.</span></span>  
  
### <a name="to-bind-an-attribute-to-a-name-column"></a><span data-ttu-id="85d50-104">이름 열에 특성을 바인딩하려면</span><span class="sxs-lookup"><span data-stu-id="85d50-104">To bind an attribute to a name column</span></span>  
  
1.  <span data-ttu-id="85d50-105">차원 디자이너에서 특성을 만들려는 차원을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="85d50-105">In Dimension Designer, open the dimension in which you want to create the attribute.</span></span>  
  
2.  <span data-ttu-id="85d50-106">**차원 구조** 탭의 **특성** 창에서 구성할 특성을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="85d50-106">On the **Dimension Structure** tab, in the **Attributes** pane, right-click the attribute that you want to configure, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="85d50-107">**속성** 창에서 **NameColumn** 속성을 찾은 다음 **(새로 만들기)** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="85d50-107">In the **Properties** window, locate the **NameColumn** property, and then select **(new)**.</span></span>  
  
4.  <span data-ttu-id="85d50-108">**개체 바인딩** 대화 상자에서 **바인딩 유형**으로 **열 바인딩**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="85d50-108">In the **Object Binding** dialog box, for **Binding type**, select **Column binding**.</span></span>  
  
5.  <span data-ttu-id="85d50-109">**원본 열** 목록에서 특성이 바인딩될 열을 선택한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="85d50-109">In the **Source column** list, select the column to which the attribute will be bound, and then click **OK**.</span></span>  
  
  
