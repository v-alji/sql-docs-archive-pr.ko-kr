---
title: SQL Server 개체의 정책 기반 관리 패싯 보기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, view facets
ms.assetid: 5f423b9f-a6c4-41a7-9d8d-8f4926ce1fb4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 9137971a79e9e5a18e0ef5d901184133a4c3eff3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648975"
---
# <a name="view-the-policy-based-management-facets-on-a-sql-server-object"></a><span data-ttu-id="27341-102">SQL Server 개체의 정책 기반 관리 패싯 보기</span><span class="sxs-lookup"><span data-stu-id="27341-102">View the Policy-Based Management Facets on a SQL Server Object</span></span>
  <span data-ttu-id="27341-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 를 사용하여 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 특정 SQL Server 개체에 적용되는 모든 정책 기반 관리 패싯을 보는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="27341-103">This topic describes how to view all of the Policy-Based Management facets applied to a specific SQL Server object in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="27341-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="27341-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="27341-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="27341-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="27341-106">보안</span><span class="sxs-lookup"><span data-stu-id="27341-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="27341-107">**다음을 사용하여 개체의 모든 패싯을 보려면:**</span><span class="sxs-lookup"><span data-stu-id="27341-107">**To view all of the facets in an object, using:**</span></span>  
  
     [<span data-ttu-id="27341-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="27341-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="27341-109">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="27341-109">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="27341-110">보안</span><span class="sxs-lookup"><span data-stu-id="27341-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="27341-111">권한</span><span class="sxs-lookup"><span data-stu-id="27341-111">Permissions</span></span>  
 <span data-ttu-id="27341-112">msdb 데이터베이스에서 PolicyAdministratorRole 역할의 멤버 자격이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="27341-112">Requires membership in the PolicyAdministratorRole role in the msdb database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="27341-113">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="27341-113">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-all-of-the-facets-in-an-object"></a><span data-ttu-id="27341-114">개체의 모든 패싯을 보려면</span><span class="sxs-lookup"><span data-stu-id="27341-114">To view all of the facets in an object</span></span>  
  
1.  <span data-ttu-id="27341-115">개체 탐색기에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스, 인스턴스 개체, 데이터베이스 또는 데이터베이스 개체를 마우스 오른쪽 단추로 클릭한 다음 **패싯**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="27341-115">In Object Explorer, right-click an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], instance object, database, or database object, and then click **Facets**.</span></span>  
  
2.  <span data-ttu-id="27341-116">**패싯 보기 –**_object_name_ 대화 상자의 **패싯** 목록에서 해당 속성을 보려면 패싯을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="27341-116">In the **View Facets -**_object_name_ dialog box, in the **Facet** list, select a facet to view its properties.</span></span> <span data-ttu-id="27341-117">이 대화 상자에서 사용할 수 있는 옵션에 대한 자세한 내용은 [View Facets Dialog Box](view-facets-dialog-box.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="27341-117">For more information on the available options in this dialog box, see [View Facets Dialog Box](view-facets-dialog-box.md).</span></span>  
  
3.  <span data-ttu-id="27341-118">완료되었으면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="27341-118">When finished, click **OK**.</span></span>  
  
  
