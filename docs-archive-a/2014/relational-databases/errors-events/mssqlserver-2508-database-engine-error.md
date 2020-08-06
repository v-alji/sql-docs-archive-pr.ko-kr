---
title: MSSQLSERVER_2508 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2508 (Database Engine error)
ms.assetid: c37d40e5-c665-4d66-a727-5cb845634fcc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 11dd1c72c8cae868b7ebcb02e72ef0db81aeafe2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731635"
---
# <a name="mssqlserver_2508"></a><span data-ttu-id="b255d-102">MSSQLSERVER_2508</span><span class="sxs-lookup"><span data-stu-id="b255d-102">MSSQLSERVER_2508</span></span>
    
## <a name="details"></a><span data-ttu-id="b255d-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="b255d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b255d-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="b255d-104">Product Name</span></span>|<span data-ttu-id="b255d-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="b255d-105">SQL Server</span></span>|  
|<span data-ttu-id="b255d-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="b255d-106">Event ID</span></span>|<span data-ttu-id="b255d-107">2508</span><span class="sxs-lookup"><span data-stu-id="b255d-107">2508</span></span>|  
|<span data-ttu-id="b255d-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="b255d-108">Event Source</span></span>|<span data-ttu-id="b255d-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="b255d-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="b255d-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="b255d-110">Component</span></span>|<span data-ttu-id="b255d-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="b255d-111">SQLEngine</span></span>|  
|<span data-ttu-id="b255d-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="b255d-112">Symbolic Name</span></span>|<span data-ttu-id="b255d-113">DBCC_OUT_OF_DATE_PAGE_OR_ROW_COUNT</span><span class="sxs-lookup"><span data-stu-id="b255d-113">DBCC_OUT_OF_DATE_PAGE_OR_ROW_COUNT</span></span>|  
|<span data-ttu-id="b255d-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="b255d-114">Message Text</span></span>|<span data-ttu-id="b255d-115">개체 "%.\*ls", 인덱스 ID %d, 파티션 ID %I64d, 할당 단위 ID %I64d(%.\*ls 유형)의 %.\*ls 개수가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b255d-115">The %.\*ls count for object "%.\*ls", index ID %d, partition ID %I64d, alloc unit ID %I64d (type %.\*ls) is incorrect.</span></span> <span data-ttu-id="b255d-116">DBCC UPDATEUSAGE를 실행하십시오.</span><span class="sxs-lookup"><span data-stu-id="b255d-116">Run DBCC UPDATEUSAGE.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="b255d-117">설명</span><span class="sxs-lookup"><span data-stu-id="b255d-117">Explanation</span></span>  
 <span data-ttu-id="b255d-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 이전 버전의 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]에서는 테이블 및 인덱스의 행 및 페이지 개수의 값이 정확하지 않게 계산될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b255d-118">In versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] before [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], the values for the table and index row counts and page counts can become incorrect.</span></span> <span data-ttu-id="b255d-119">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이전 버전에서 만든 데이터베이스에는 올바르지 않은 개수가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b255d-119">Databases that were created on versions prior to [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] may contain incorrect counts.</span></span> <span data-ttu-id="b255d-120">이러한 오류를 검색하고 오류가 발견되면 이 경고 메시지를 반환하도록 DBCC CHECKDB가 개선되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b255d-120">DBCC CHECKDB has been enhanced to detect these errors and returns this warning message when the error encountered.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b255d-121">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="b255d-121">User Action</span></span>  
 <span data-ttu-id="b255d-122">지정된 개체나 인덱스 또는 개체가 포함된 데이터베이스를 대상으로 DBCC UPDATEUSAGE를 실행하여 잘못된 개수를 수정하십시오.</span><span class="sxs-lookup"><span data-stu-id="b255d-122">Run DBCC UPDATEUSAGE against the specified object or index, or against the database in which the object is contained to correct the invalid counts.</span></span>  
  
  
