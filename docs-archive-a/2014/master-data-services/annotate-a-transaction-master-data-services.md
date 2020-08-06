---
title: 트랜잭션에 주석 추가(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- annotations [Master Data Services], for transactions
ms.assetid: f5a6b2ca-56de-4e42-9da8-fba0ac3e8d92
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c384f4241d0ddcd78fd8942fe28da8c0b5b1e77c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734235"
---
# <a name="annotate-a-transaction-master-data-services"></a><span data-ttu-id="51d34-102">트랜잭션에 주석 추가(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="51d34-102">Annotate a Transaction (Master Data Services)</span></span>
  <span data-ttu-id="51d34-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 기록 목적으로 트랜잭션에 대한 지원 정보를 제공하려면 트랜잭션에 주석을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="51d34-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], annotate a transaction when you want to provide supporting details about the transaction for historical purposes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="51d34-104">주석은 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="51d34-104">You cannot delete annotations.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="51d34-105">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="51d34-105">Prerequisites</span></span>  
  
-   <span data-ttu-id="51d34-106">만든 트랜잭션에 주석을 추가하려면 **탐색기** 기능 영역에 대한 액세스 권한과 주석을 추가할 모델 개체에 대한 **업데이트** 이상의 사용 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="51d34-106">To annotate transactions that you created, you must have permission to access the **Explorer** functional area, and have a minimum of **Update** permission to the model object you want to annotate.</span></span>  
  
-   <span data-ttu-id="51d34-107">모든 사용자를 위해 트랜잭션에 주석을 추가하려면 **버전 관리** 기능 영역에 액세스할 수 있는 권한이 있어야 하며 모델 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="51d34-107">To annotate transactions for all users, you must have permission to access the **Version Management** functional area and be a model administrator.</span></span> <span data-ttu-id="51d34-108">자세한 내용은 [관리자 &#40;MDS(Master Data Services)&#41;](administrators-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="51d34-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-annotate-a-transaction-in-explorer"></a><span data-ttu-id="51d34-109">탐색기에서 트랜잭션에 주석을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="51d34-109">To annotate a transaction in Explorer</span></span>  
  
1.  <span data-ttu-id="51d34-110">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 홈 페이지의 **모델** 목록에서 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="51d34-110">On the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] home page, from the **Model** list, select a model.</span></span>  
  
2.  <span data-ttu-id="51d34-111">**버전** 목록에서 버전을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="51d34-111">From the **Version** list, select a version.</span></span>  
  
3.  <span data-ttu-id="51d34-112">**탐색기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="51d34-112">Click **Explorer**.</span></span>  
  
4.  <span data-ttu-id="51d34-113">메뉴 모음에서 **엔터티** 를 가리키고 주석을 추가할 트랜잭션을 가진 멤버를 포함하는 엔터티의 이름을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="51d34-113">From the menu bar, point to **Entities** and click the entity that contains the member with a transaction you want to annotate.</span></span>  
  
5.  <span data-ttu-id="51d34-114">표에서 멤버의 행을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="51d34-114">In the grid, click the row of the member.</span></span>  
  
6.  <span data-ttu-id="51d34-115">**트랜잭션 보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="51d34-115">Click **View Transactions**.</span></span>  
  
7.  <span data-ttu-id="51d34-116">**트랜잭션 보기** 대화 상자에서 주석을 추가할 트랜잭션을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="51d34-116">In the **View Transactions** dialog box, click the transaction you want to annotate.</span></span>  
  
8.  <span data-ttu-id="51d34-117">대화 상자 아래쪽의 상자에 주석을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="51d34-117">In the box at the bottom of the dialog box, type your annotation.</span></span>  
  
9. <span data-ttu-id="51d34-118">**주석 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="51d34-118">Click **Add Annotation**.</span></span> <span data-ttu-id="51d34-119">주석이 **주석** 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="51d34-119">The annotation is displayed in the **Annotations** pane.</span></span>  
  
### <a name="to-annotate-a-transaction-in-version-management-administrators-only"></a><span data-ttu-id="51d34-120">버전 관리에서 트랜잭션에 주석을 추가하려면(관리자에만 해당)</span><span class="sxs-lookup"><span data-stu-id="51d34-120">To annotate a transaction in Version Management (administrators only)</span></span>  
  
1.  <span data-ttu-id="51d34-121">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 홈 페이지에서 **버전 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="51d34-121">On the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] home page, click **Version Management**.</span></span>  
  
2.  <span data-ttu-id="51d34-122">메뉴 모음에서 **트랜잭션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="51d34-122">On the menu bar, click **Transactions**.</span></span>  
  
3.  <span data-ttu-id="51d34-123">**트랜잭션** 창의 표에서 주석을 추가할 트랜잭션의 행을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="51d34-123">In the **Transactions** pane, click the row in the grid for the transaction you want to annotate.</span></span>  
  
4.  <span data-ttu-id="51d34-124">**트랜잭션 주석** 창의 **주석** 상자에 주석을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="51d34-124">In the **Transaction Annotations** pane, in the **Annotation** box, type your annotation.</span></span>  
  
5.  <span data-ttu-id="51d34-125">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="51d34-125">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51d34-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="51d34-126">See Also</span></span>  
 <span data-ttu-id="51d34-127">[주석 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/annotations-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="51d34-127">[Annotations &#40;Master Data Services&#41;](../../2014/master-data-services/annotations-master-data-services.md) </span></span>  
 [<span data-ttu-id="51d34-128">트랜잭션&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="51d34-128">Transactions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/transactions-master-data-services.md)  
  
  
