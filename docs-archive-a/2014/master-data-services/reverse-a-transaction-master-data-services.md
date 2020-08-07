---
title: 트랜잭션 되돌리기(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- transactions [Master Data Services], reversing
ms.assetid: 6f7c3f07-0f64-4283-8c9c-93facd00a046
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: fb5b1b0932b65b1d6f8fe7b1bc842836e21aaca6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730771"
---
# <a name="reverse-a-transaction-master-data-services"></a><span data-ttu-id="b0a9e-102">트랜잭션 되돌리기(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="b0a9e-102">Reverse a Transaction (Master Data Services)</span></span>
  <span data-ttu-id="b0a9e-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 동작을 취소해야 할 경우 관리자가 트랜잭션을 되돌릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b0a9e-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], administrators can reverse a transaction when an action needs to be undone.</span></span> <span data-ttu-id="b0a9e-104">트랜잭션의 예로 특성 값 변경, 계층 이동 또는 멤버 삭제가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b0a9e-104">Examples of transactions are attribute value changes, hierarchy moves, or member deletions.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b0a9e-105">필수 조건</span><span class="sxs-lookup"><span data-stu-id="b0a9e-105">Prerequisites</span></span>  
  
-   <span data-ttu-id="b0a9e-106">**버전 관리** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0a9e-106">You must have permission to access the **Version Management** functional area.</span></span>  
  
-   <span data-ttu-id="b0a9e-107">모델 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0a9e-107">You must be a model administrator.</span></span> <span data-ttu-id="b0a9e-108">자세한 내용은 [관리자 &#40;MDS(Master Data Services)&#41;](administrators-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b0a9e-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-reverse-a-transaction"></a><span data-ttu-id="b0a9e-109">트랜잭션을 되돌리려면</span><span class="sxs-lookup"><span data-stu-id="b0a9e-109">To reverse a transaction</span></span>  
  
1.  <span data-ttu-id="b0a9e-110">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 홈 페이지에서 **버전 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b0a9e-110">On the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] home page, click **Version Management**.</span></span>  
  
2.  <span data-ttu-id="b0a9e-111">메뉴 모음에서 **트랜잭션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b0a9e-111">On the menu bar, click **Transactions**.</span></span>  
  
3.  <span data-ttu-id="b0a9e-112">**트랜잭션** 페이지의 **모델** 목록에서 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b0a9e-112">On the **Transactions** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="b0a9e-113">**버전** 목록에서 버전을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b0a9e-113">From the **Version** list, select a version.</span></span>  
  
5.  <span data-ttu-id="b0a9e-114">트랜잭션의 표에서 되돌릴 행을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b0a9e-114">Click the row in the grid for the transaction you want to reverse.</span></span>  
  
6.  <span data-ttu-id="b0a9e-115">**트랜잭션 되돌리기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b0a9e-115">Click **Reverse Transaction**.</span></span>  
  
7.  <span data-ttu-id="b0a9e-116">확인 대화 상자에서 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b0a9e-116">In the confirmation dialog box, click **OK**.</span></span> <span data-ttu-id="b0a9e-117">되돌린 트랜잭션을 기록하기 위해 또 다른 트랜잭션이 표에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="b0a9e-117">Another transaction is added to the grid to record the reversed transaction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0a9e-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b0a9e-118">See Also</span></span>  
 <span data-ttu-id="b0a9e-119">[트랜잭션 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/transactions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="b0a9e-119">[Transactions &#40;Master Data Services&#41;](../../2014/master-data-services/transactions-master-data-services.md) </span></span>  
 [<span data-ttu-id="b0a9e-120">멤버 또는 컬렉션 다시 활성화&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="b0a9e-120">Reactivate a Member or Collection &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/reactivate-a-member-or-collection-master-data-services.md)  
  
  
