---
title: Management Studio에서 속성 창 사용
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- viewing properties
- Properties window [SQL Server Management Studio]
- complex properties [SQL Server Management Studio]
ms.assetid: 903d4aca-f57c-43d9-a893-702eceaa7004
author: rothja
ms.author: jroth
ms.openlocfilehash: 5030bf85fc87482b11e91967ff8fb1baf77a213e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660465"
---
# <a name="use-the-properties-window-in-management-studio"></a><span data-ttu-id="0d6a8-102">Management Studio에서 속성 창 사용</span><span class="sxs-lookup"><span data-stu-id="0d6a8-102">Use the Properties Window in Management Studio</span></span>
  <span data-ttu-id="0d6a8-103">속성 창은 연결 또는 실행 계획 연산자와 같은 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]의 항목의 상태와 테이블, 뷰, 디자이너 등과 같은 데이터베이스 개체에 대한 정보를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0d6a8-103">The Properties window describes the state of an item in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], such as a connection or a Showplan operator, and information about database objects such as tables, views, and designers.</span></span>  
  
 <span data-ttu-id="0d6a8-104">속성 창을 사용하여 현재 연결의 속성을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d6a8-104">You can use the Properties window to view the properties of the current connection.</span></span> <span data-ttu-id="0d6a8-105">대부분의 속성은 속성 창에서 읽기 전용이지만 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]의 다른 위치에서 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d6a8-105">Many properties are read-only in the Properties window but can be changed elsewhere in the [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="0d6a8-106">예를 들어 쿼리의 데이터베이스 속성은 속성 창에서 읽기 전용이지만 도구 모음에서 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d6a8-106">For example, the Database property of a query is read-only in the Properties window, but can be changed on the tool bar.</span></span>  
  
### <a name="to-view-properties-using-the-properties-window"></a><span data-ttu-id="0d6a8-107">속성 창을 사용하여 속성을 보려면</span><span class="sxs-lookup"><span data-stu-id="0d6a8-107">To view properties using the Properties window</span></span>  
  
1.  <span data-ttu-id="0d6a8-108">속성 창이 표시되지 않은 경우 **보기** 메뉴에서 **속성 창** 을 클릭하거나 F4 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="0d6a8-108">If the Properties window is not visible, click **Properties Window** on the **View** menu, or press F4.</span></span>  
  
2.  <span data-ttu-id="0d6a8-109">보려는 개체에 포커스를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="0d6a8-109">Set the focus on the object that you want to view.</span></span>  
  
3.  <span data-ttu-id="0d6a8-110">속성 창에서 특정 속성을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="0d6a8-110">Look for a specific property in the Properties window.</span></span>  
  
### <a name="to-view-connection-properties-of-a-query-window"></a><span data-ttu-id="0d6a8-111">쿼리 창의 연결 속성을 보려면</span><span class="sxs-lookup"><span data-stu-id="0d6a8-111">To view connection properties of a query window</span></span>  
  
1.  <span data-ttu-id="0d6a8-112">속성 창이 표시되지 않은 경우 **보기** 메뉴에서 **속성 창** 을 클릭하거나 F4 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="0d6a8-112">If the Properties window is not visible, click **Properties Window** on the **View** menu, or press F4.</span></span>  
  
2.  <span data-ttu-id="0d6a8-113">속성 창에서 모든 연결 속성을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d6a8-113">In the Properties window, you can see all the connection properties.</span></span>  
  
### <a name="to-view-the-properties-of-a-showplan-operator"></a><span data-ttu-id="0d6a8-114">실행 계획 연산자의 속성을 보려면</span><span class="sxs-lookup"><span data-stu-id="0d6a8-114">To view the properties of a Showplan operator</span></span>  
  
1.  <span data-ttu-id="0d6a8-115">**쿼리** 메뉴에서 **실제 실행 계획 포함**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0d6a8-115">On the **Query** menu, click **Include Actual Execution Plan**.</span></span>  
  
2.  <span data-ttu-id="0d6a8-116">SQL 쿼리 편집기에서 쿼리를 입력 및 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="0d6a8-116">In the SQL Query Editor, type and execute a query.</span></span>  
  
3.  <span data-ttu-id="0d6a8-117">속성 창이 표시되지 않은 경우 **보기** 메뉴에서 **속성 창** 을 클릭하거나 F4 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="0d6a8-117">If the Properties window is not visible, click **Properties Window** on the **View** menu, or press F4.</span></span>  
  
4.  <span data-ttu-id="0d6a8-118">SQL 쿼리 편집기의 **실행 계획** 탭에서 연산자의 아이콘을 클릭하여 속성 창에서 연산자에 대한 정보를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="0d6a8-118">On the **Execution plan** tab of the SQL Query Editor click the icons of the operators to view information about the operators in the Properties window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d6a8-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0d6a8-119">See Also</span></span>  
 [<span data-ttu-id="0d6a8-120">속성 창&#40;Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="0d6a8-120">Properties Window &#40;Management Studio&#41;</span></span>](../../ssms/properties-window-management-studio.md)  
  
  
