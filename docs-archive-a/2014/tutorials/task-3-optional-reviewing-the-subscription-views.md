---
title: '작업 3 (선택 사항): 구독 뷰 검토 | Microsoft Docs'
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 3f1d3eb7-2baa-4215-b040-0b41e3d10740
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 35cf0c246ab778b46a2ceaa2b6ff6fad02d0b670
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647386"
---
# <a name="task-3-optional-reviewing-the-subscription-views"></a><span data-ttu-id="fbaa7-102">태스크 3(선택 사항): 구독 뷰 검토</span><span class="sxs-lookup"><span data-stu-id="fbaa7-102">Task 3 (Optional): Reviewing the Subscription Views</span></span>
  <span data-ttu-id="fbaa7-103">이 작업에서는 SQL Server Management Studio를 사용하여 SQL 뷰가 만들어졌는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="fbaa7-103">In this task, you confirm that the SQL views are created by using SQL Server Management Studio.</span></span>

1.  <span data-ttu-id="fbaa7-104">**SQL Server Management Studio**를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="fbaa7-104">Launch **SQL Server Management Studio**.</span></span> <span data-ttu-id="fbaa7-105">**시작** 단추를 클릭 하 고 **모든 프로그램**, **Microsoft SQL Server 2012**를 차례로 클릭 한 다음 **SQL Server Management Studio**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="fbaa7-105">Click the **Start** button, click **All Programs**, click **Microsoft SQL Server 2012**, and then click **SQL Server Management Studio**.</span></span>

2.  <span data-ttu-id="fbaa7-106">**서버에 연결** 창에서 **서버 유형** 을 **데이터베이스 엔진**로 설정 하 고 **서버 이름을** 입력 하거나 **(로컬)** 을 선택 하 고 적절 한 **인증**을 선택 하 고 **연결**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="fbaa7-106">In the **Connect to Server** window, set **Server Type** to **Database Engine**, type the **server name** (or select **(local)**, and select appropriate **authentication**, and click **Connect**.</span></span>

3.  <span data-ttu-id="fbaa7-107">**개체 탐색기** 창에서 **데이터베이스**, **MDS**, **보기**를 차례로 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="fbaa7-107">In the **Object Explorer** pane, expand **Databases**, expand **MDS**, and then expand **Views**.</span></span>

4.  <span data-ttu-id="fbaa7-108">Mdm이 표시 되는지 확인 **합니다. 목록의 공급자** 뷰입니다.</span><span class="sxs-lookup"><span data-stu-id="fbaa7-108">Confirm that you see the **mdm.Suppliers** view in the list.</span></span>

     <span data-ttu-id="fbaa7-109">![SQL Server Management Studio - mdm.Suppliers 뷰](../../2014/tutorials/media/et-reviewingthesubscriptionviews.jpg "SQL Server Management Studio - mdm.Suppliers 뷰")</span><span class="sxs-lookup"><span data-stu-id="fbaa7-109">![SQL Server Management Studio - mdm.Suppliers View](../../2014/tutorials/media/et-reviewingthesubscriptionviews.jpg "SQL Server Management Studio - mdm.Suppliers View")</span></span>

## <a name="next-step"></a><span data-ttu-id="fbaa7-110">다음 단계</span><span class="sxs-lookup"><span data-stu-id="fbaa7-110">Next Step</span></span>
 [<span data-ttu-id="fbaa7-111">태스크 4: SQL Server Data Tools를 사용하여 SSIS 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="fbaa7-111">Task 4: Creating an SSIS Project using SQL Server Data Tools</span></span>](../../2014/tutorials/task-4-creating-an-ssis-project-using-sql-server-data-tools.md)