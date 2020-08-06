---
title: 축 지정 (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], axes
- XPath queries [SQLXML], location paths
- self axis
- attribute axis [SQLXML]
- axis [SQLXML]
- child axis
- parent axis
- location path for XPath query
- axes [SQLXML]
ms.assetid: 65631795-3389-40cf-90ea-85e9438956c5
author: rothja
ms.author: jroth
ms.openlocfilehash: 5e43281fe31d323a7eea19e749b80b59458752b7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651581"
---
# <a name="specifying-an-axis-sqlxml-40"></a><span data-ttu-id="93079-102">축 지정(SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="93079-102">Specifying an Axis (SQLXML 4.0)</span></span>
    
-   <span data-ttu-id="93079-103">축은 위치 단계에서 선택되는 노드와 컨텍스트 노드 간의 트리 관계를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="93079-103">The axis specifies the tree relationship between the nodes selected by the location step and the context node.</span></span> <span data-ttu-id="93079-104">다음 축이 지원 됩니다.`child`</span><span class="sxs-lookup"><span data-stu-id="93079-104">The following axes are supported:  `child`</span></span>  
  
     <span data-ttu-id="93079-105">컨텍스트 노드의 자식을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="93079-105">Contains the child of the context node.</span></span>  
  
     <span data-ttu-id="93079-106">다음 XPath 식 (위치 경로)은 현재 컨텍스트 노드에서 모든 자식을 선택 합니다 **\<Customer>** .</span><span class="sxs-lookup"><span data-stu-id="93079-106">The following XPath expression (location path) selects from the current context node all the **\<Customer>** children:</span></span>  
  
    ```  
    child::Customer  
    ```  
  
     <span data-ttu-id="93079-107">다음 XPath 쿼리에서`child`는 축이고</span><span class="sxs-lookup"><span data-stu-id="93079-107">In the following XPath query, `child` is the axis.</span></span> <span data-ttu-id="93079-108">`Customer`는 노드 테스트입니다.</span><span class="sxs-lookup"><span data-stu-id="93079-108">`Customer` is the node test.</span></span>  
  
-   `parent`  
  
     <span data-ttu-id="93079-109">컨텍스트 노드의 부모를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="93079-109">Contains the parent of the context node.</span></span>  
  
     <span data-ttu-id="93079-110">다음 XPath 식은 자식의 모든 부모를 선택 합니다 **\<Customer>** **\<Order>** .</span><span class="sxs-lookup"><span data-stu-id="93079-110">The following XPath expression selects all the **\<Customer>** parents of the **\<Order>** children:</span></span>  
  
    ```  
    child::Customer/child::Order[parent::Customer/@customerID="ALFKI"]  
    ```  
  
     <span data-ttu-id="93079-111">이것은 `child::Customer`를 지정하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="93079-111">This is the same as specifying `child::Customer`.</span></span> <span data-ttu-id="93079-112">이 XPath 쿼리에서 `child`와 `parent`는 축이고</span><span class="sxs-lookup"><span data-stu-id="93079-112">In this XPath query, `child` and `parent` are the axes.</span></span> <span data-ttu-id="93079-113">`Customer`와 `Order`는 노드 테스트입니다.</span><span class="sxs-lookup"><span data-stu-id="93079-113">`Customer` and `Order` are the node tests.</span></span>  
  
-   `attribute`  
  
     <span data-ttu-id="93079-114">컨텍스트 노드의 특성을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="93079-114">Contains the attribute of the context node.</span></span>  
  
     <span data-ttu-id="93079-115">다음 XPath 식은 컨텍스트 노드의 **CustomerID** 특성을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="93079-115">The following XPath expression selects the **CustomerID** attribute of the context node:</span></span>  
  
    ```  
    attribute::CustomerID  
    ```  
  
-   `self`  
  
     <span data-ttu-id="93079-116">컨텍스트 노드 자신을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="93079-116">Contains the context node itself.</span></span>  
  
     <span data-ttu-id="93079-117">다음 XPath 식은 노드인 경우 현재 노드를 선택 합니다 **\<Order>** .</span><span class="sxs-lookup"><span data-stu-id="93079-117">The following XPath expression selects the current node if it is the **\<Order>** node:</span></span>  
  
    ```  
    self::Order  
    ```  
  
     <span data-ttu-id="93079-118">이 XPath 쿼리에서 `self`는 축이고 `Order`는 노드 테스트입니다.</span><span class="sxs-lookup"><span data-stu-id="93079-118">In this XPath query, `self` is the axis and `Order` is the node test.</span></span>  
  
  
