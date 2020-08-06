---
title: 개체 탐색기에서 시스템 개체 숨기기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- hiding system objects
- system objects [SQL Server]
- objects [SQL Server], hiding
- Object Explorer, hiding objects
ms.assetid: c01d8804-838c-4f75-b78c-80e41e4fffdc
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1e039446191154144dd6660fa6e8d3b4b65d1013
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638519"
---
# <a name="hide-system-objects-in-object-explorer"></a><span data-ttu-id="6be1a-102">개체 탐색기에서 시스템 개체 숨기기</span><span class="sxs-lookup"><span data-stu-id="6be1a-102">Hide System Objects in Object Explorer</span></span>
  <span data-ttu-id="6be1a-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 를 사용하여 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]의 개체 탐색기에서 시스템 개체를 숨기는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6be1a-103">This topic describes how to hide system objects in Object Explorer in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="6be1a-104">개체 탐색기의 **데이터베이스** 노드에는 시스템 데이터베이스와 같은 시스템 개체가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6be1a-104">The **Databases** node of Object Explorer contains system objects such as the system databases.</span></span> <span data-ttu-id="6be1a-105">**도구**/**옵션** 페이지를 사용하여 시스템 개체를 숨길 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6be1a-105">Use the **Tools**/**Options** pages to hide the system objects.</span></span> <span data-ttu-id="6be1a-106">시스템 함수 및 시스템 데이터 형식과 같은 일부 시스템 개체는 이 설정의 영향을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6be1a-106">Some system objects, such as system functions and system data types, are not affected by this setting.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="6be1a-107">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="6be1a-107">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-hide-system-objects-in-object-explorer"></a><span data-ttu-id="6be1a-108">개체 탐색기에서 시스템 개체를 숨기려면</span><span class="sxs-lookup"><span data-stu-id="6be1a-108">To hide system objects in Object Explorer</span></span>  
  
1.  <span data-ttu-id="6be1a-109">**도구** 메뉴에서 **옵션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6be1a-109">On the **Tools** menu, click **Options**.</span></span>  
  
2.  <span data-ttu-id="6be1a-110">**환경/시작** 페이지에서 **개체 탐색기에서 시스템 개체 숨기기**를 선택한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6be1a-110">On the **Environment/Startup** page, select **Hide system objects in Object Explorer**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="6be1a-111">**SQL Server Management Studio** 대화 상자에서 **확인** 을 클릭합니다. 변경 내용을 적용하기 위해서는 SQL Server Management Studio를 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6be1a-111">In the **SQL Server Management Studio** dialog box, click **OK** to acknowledge that SQL Server Management Studio must be restarted for this change to take effect.</span></span>  
  
4.  <span data-ttu-id="6be1a-112">SQL Server Management Studio를 닫고 다시 엽니다.</span><span class="sxs-lookup"><span data-stu-id="6be1a-112">Close and reopen SQL Server Management Studio.</span></span>  
  
  
