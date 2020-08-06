---
title: 데이터베이스 잠금 및 잠금 해제 (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- locking [XML for Analysis]
- XML for Analysis, locking
- XMLA, locking
- unlocking objects
ms.assetid: 451afa58-ce03-4ecc-8dd3-9e7e8559b5f1
author: minewiskan
ms.author: owend
ms.openlocfilehash: 96afa94f7c9c20072ae88b09a436d079ce0478ae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735555"
---
# <a name="locking-and-unlocking-databases-xmla"></a><span data-ttu-id="5fd2d-102">데이터베이스 잠금 및 잠금 해제(XMLA)</span><span class="sxs-lookup"><span data-stu-id="5fd2d-102">Locking and Unlocking Databases (XMLA)</span></span>
  <span data-ttu-id="5fd2d-103">XML for Analysis (XMLA)의 [잠금](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla) 및 [잠금 해제](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla) 명령을 사용 하 여 데이터베이스를 잠그거나 잠금 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5fd2d-103">You can lock and unlock databases using, respectively, the [Lock](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla) and [Unlock](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla) commands in XML for Analysis (XMLA).</span></span> <span data-ttu-id="5fd2d-104">일반적으로 다른 XMLA 명령은 실행 중 해당 명령을 수행하는 데 필요할 경우 자동으로 개체를 잠그거나 잠금 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd2d-104">Typically, other XMLA commands automatically lock and unlock objects as needed to complete the command during execution.</span></span> <span data-ttu-id="5fd2d-105">[일괄 처리](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/batch-element-xmla) 명령과 같이 단일 트랜잭션 내에서 여러 명령을 수행 하기 위해 데이터베이스를 명시적으로 잠그거나 잠금 해제 하는 동시에 다른 응용 프로그램에서 데이터베이스에 쓰기 트랜잭션을 커밋하지 못하게 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5fd2d-105">You can explicitly lock or unlock a database to perform multiple commands within a single transaction, such as a [Batch](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/batch-element-xmla) command, while preventing other applications from committing a write transaction to the database.</span></span>  
  
## <a name="locking-databases"></a><span data-ttu-id="5fd2d-106">데이터베이스 잠금</span><span class="sxs-lookup"><span data-stu-id="5fd2d-106">Locking Databases</span></span>  
 <span data-ttu-id="5fd2d-107">`Lock` 명령은 현재 활성 트랜잭션 컨텍스트 내에서 공유되거나 배타적으로 사용되는 개체를 잠급니다.</span><span class="sxs-lookup"><span data-stu-id="5fd2d-107">The `Lock` command locks an object, either for shared or exclusive use, within the context of the currently active transaction.</span></span> <span data-ttu-id="5fd2d-108">개체가 잠겨 있으면 잠금을 해제할 때까지 트랜잭션을 커밋할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5fd2d-108">A lock on an object prevents transactions from committing until the lock is removed.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="5fd2d-109">에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 공유 잠금과 배타적 잠금 이라는 두 가지 잠금 유형을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd2d-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] supports two types of locks, shared locks and exclusive locks.</span></span> <span data-ttu-id="5fd2d-110">에서 지원 되는 잠금 유형에 대 한 자세한 내용은 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] [모드 요소 &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/mode-element-xmla)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5fd2d-110">For more information about the lock types supported by [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], see [Mode Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/mode-element-xmla).</span></span>  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]<span data-ttu-id="5fd2d-111">는 데이터베이스 잠금만 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd2d-111">allows only databases to be locked.</span></span> <span data-ttu-id="5fd2d-112">[Object](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) 요소는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스에 대한 개체 참조를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd2d-112">The [Object](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) element must contain an object reference to an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="5fd2d-113">`Object` 요소를 지정하지 않거나 `Object` 요소가 데이터베이스 이외의 개체를 참조하면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd2d-113">If the `Object` element is not specified or if the `Object` element refers to an object other than a database, an error occurs.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="5fd2d-114">데이터베이스 관리자 또는 서버 관리자만 명시적으로 `Lock` 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5fd2d-114">Only database administrators or server administrators can explicitly issue a `Lock` command.</span></span>  
  
 <span data-ttu-id="5fd2d-115">다른 명령을 실행하면 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스에서 `Lock` 명령이 암시적으로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="5fd2d-115">Other commands implicitly issue a `Lock` command on an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="5fd2d-116">데이터베이스의 데이터 또는 메타데이터를 읽는 작업(예: [Discover](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover) 명령을 실행하는 [Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) 메서드 또는 [Statement](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/statement-element-xmla) 메서드)을 수행하면 데이터베이스에서 암시적으로 공유 잠금이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="5fd2d-116">Any operation that reads data or metadata from a database, such as any [Discover](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover) method or an [Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) method running a [Statement](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/statement-element-xmla) command, implicitly issues a shared lock on the database.</span></span> <span data-ttu-id="5fd2d-117">Alter 명령을 실행 하는 메서드와 같이 데이터 또는 메타 데이터의 변경 내용을 데이터베이스의 개체에 커밋하는 트랜잭션은 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] `Execute` 암시적 [Alter](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla) 으로 데이터베이스에 대 한 배타적 잠금을 발급 합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd2d-117">Any transaction that commits changes in data or metadata to an object on an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database, such as an `Execute` method running an [Alter](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla) command, implicitly issues an exclusive lock on the database.</span></span>  
  
## <a name="unlocking-objects"></a><span data-ttu-id="5fd2d-118">개체 잠금 해제</span><span class="sxs-lookup"><span data-stu-id="5fd2d-118">Unlocking Objects</span></span>  
 <span data-ttu-id="5fd2d-119">`Unlock` 명령은 현재 활성 트랜잭션 컨텍스트 내에서 설정된 잠금을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd2d-119">The `Unlock` command removes a lock established within the context of the currently active transaction.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="5fd2d-120">데이터베이스 관리자 또는 서버 관리자만 명시적으로 `Unlock` 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5fd2d-120">Only database administrators or server administrators can explicitly issue an `Unlock` command.</span></span>  
  
 <span data-ttu-id="5fd2d-121">모든 잠금은 현재 트랜잭션의 컨텍스트에 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="5fd2d-121">All locks are held in the context of the current transaction.</span></span> <span data-ttu-id="5fd2d-122">현재 트랜잭션이 커밋 또는 롤백되면 해당 트랜잭션 내에 정의된 모든 잠금이 자동으로 해제됩니다.</span><span class="sxs-lookup"><span data-stu-id="5fd2d-122">When the current transaction is committed or rolled back, all locks defined within the transaction are automatically released.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fd2d-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5fd2d-123">See Also</span></span>  
 <span data-ttu-id="5fd2d-124">[Lock 요소 &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla) </span><span class="sxs-lookup"><span data-stu-id="5fd2d-124">[Lock Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla) </span></span>  
 <span data-ttu-id="5fd2d-125">[XMLA&#41;요소 &#40;잠금 해제](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla) </span><span class="sxs-lookup"><span data-stu-id="5fd2d-125">[Unlock Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla) </span></span>  
 [<span data-ttu-id="5fd2d-126">Analysis Services에서 XMLA를 사용하여 개발</span><span class="sxs-lookup"><span data-stu-id="5fd2d-126">Developing with XMLA in Analysis Services</span></span>](developing-with-xmla-in-analysis-services.md)  
  
  
