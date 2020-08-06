---
title: 정책 기반 관리 패싯의 속성 보기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, view facet properties
ms.assetid: 022a244c-c2e7-4467-b9a2-c7a27859be22
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ea24ff2768ecaeec426a8689455912d848b54813
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648974"
---
# <a name="view-the-properties-of-a-policy-based-management-facet"></a><span data-ttu-id="aa9ed-102">정책 기반 관리 패싯의 속성 보기</span><span class="sxs-lookup"><span data-stu-id="aa9ed-102">View the Properties of a Policy-Based Management Facet</span></span>
  <span data-ttu-id="aa9ed-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 를 사용하여 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 정책 기반 관리 패싯의 속성을 보는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="aa9ed-103">This topic describes how to view the properties of a Policy-Based Management facet in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="aa9ed-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="aa9ed-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="aa9ed-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="aa9ed-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="aa9ed-106">보안</span><span class="sxs-lookup"><span data-stu-id="aa9ed-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="aa9ed-107">**다음을 사용하여 패싯의 속성을 보려면:**</span><span class="sxs-lookup"><span data-stu-id="aa9ed-107">**To view the properties of a facet, using:**</span></span>  
  
     [<span data-ttu-id="aa9ed-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="aa9ed-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="aa9ed-109">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="aa9ed-109">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="aa9ed-110">보안</span><span class="sxs-lookup"><span data-stu-id="aa9ed-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="aa9ed-111">권한</span><span class="sxs-lookup"><span data-stu-id="aa9ed-111">Permissions</span></span>  
 <span data-ttu-id="aa9ed-112">msdb 데이터베이스에서 PolicyAdministratorRole 역할의 멤버 자격이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="aa9ed-112">Requires membership in the PolicyAdministratorRole role in the msdb database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="aa9ed-113">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="aa9ed-113">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-the-properties-of-a-facet"></a><span data-ttu-id="aa9ed-114">패싯의 속성을 보려면</span><span class="sxs-lookup"><span data-stu-id="aa9ed-114">To view the properties of a facet</span></span>  
  
1.  <span data-ttu-id="aa9ed-115">**개체 탐색기**에서 더하기 기호를 클릭하여 보려는 속성이 지정된 패싯이 들어 있는 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="aa9ed-115">In **Object Explorer**, click the plus sign to expand the server that contains the facet whose properties you want to view.</span></span>  
  
2.  <span data-ttu-id="aa9ed-116">더하기 기호를 클릭하여 **관리** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="aa9ed-116">Click the plus sign to expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="aa9ed-117">더하기 기호를 클릭하여 **정책 관리**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="aa9ed-117">Click the plus sign to expand **Policy Management**.</span></span>  
  
4.  <span data-ttu-id="aa9ed-118">더하기 기호를 클릭하여 **패싯** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="aa9ed-118">Click the plus sign to expand the **Facets** folder.</span></span>  
  
5.  <span data-ttu-id="aa9ed-119">보려는 속성이 지정된 패싯을 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="aa9ed-119">Right-click the facet whose properties you want to view and select **Properties**.</span></span> <span data-ttu-id="aa9ed-120">**패싯 속성-**_facet_name_ 대화 상자에서 사용할 수 있는 옵션에 대 한 자세한 내용은 [패싯 속성 대화 상자, 일반 페이지](../../integration-services/general-page-of-integration-services-designers-options.md), [패싯 속성 대화 상자, 종속 정책 페이지](facet-properties-dialog-box-dependent-policies-page.md)및 [패싯 속성 대화 상자, 종속 조건 페이지](facet-properties-dialog-box-dependent-conditions-page.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="aa9ed-120">For more information on the available options in the **Facet Properties -**_facet_name_ dialog box, see [Facet Properties Dialog Box, General Page](../../integration-services/general-page-of-integration-services-designers-options.md), [Facet Properties Dialog Box, Dependent Policies Page](facet-properties-dialog-box-dependent-policies-page.md), and [Facet Properties Dialog Box, Dependent Conditions Page](facet-properties-dialog-box-dependent-conditions-page.md).</span></span>  
  
6.  <span data-ttu-id="aa9ed-121">완료되면 **닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="aa9ed-121">When finished, click **Close**.</span></span>  
  
  
