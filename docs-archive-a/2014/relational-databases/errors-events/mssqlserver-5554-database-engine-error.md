---
title: MSSQLSERVER_5554 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 5554 (Database Engine error)
ms.assetid: 7134bbe5-d240-4a98-85ce-b13cc8ae9b0e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5095a50f257abafb6ebde97bb32c57bc71fc4e09
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651716"
---
# <a name="mssqlserver_5554"></a><span data-ttu-id="7be79-102">MSSQLSERVER_5554</span><span class="sxs-lookup"><span data-stu-id="7be79-102">MSSQLSERVER_5554</span></span>
    
## <a name="details"></a><span data-ttu-id="7be79-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="7be79-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7be79-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="7be79-104">Product Name</span></span>|<span data-ttu-id="7be79-105">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="7be79-105">MSSQLSERVER</span></span>|  
|<span data-ttu-id="7be79-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="7be79-106">Event ID</span></span>|<span data-ttu-id="7be79-107">5554</span><span class="sxs-lookup"><span data-stu-id="7be79-107">5554</span></span>|  
|<span data-ttu-id="7be79-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="7be79-108">Event Source</span></span>|<span data-ttu-id="7be79-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="7be79-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="7be79-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="7be79-110">Component</span></span>|<span data-ttu-id="7be79-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="7be79-111">SQLEngine</span></span>|  
|<span data-ttu-id="7be79-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="7be79-112">Symbolic Name</span></span>|<span data-ttu-id="7be79-113">FS_MINIVER_OVERFLOW</span><span class="sxs-lookup"><span data-stu-id="7be79-113">FS_MINIVER_OVERFLOW</span></span>|  
|<span data-ttu-id="7be79-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="7be79-114">Message Text</span></span>|<span data-ttu-id="7be79-115">단일 파일에 대한 총 버전 수가 파일 시스템에 설정된 최대치에 도달했습니다.</span><span class="sxs-lookup"><span data-stu-id="7be79-115">The total number of versions for a single file has reached the maximum limit set by the file system.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="7be79-116">설명</span><span class="sxs-lookup"><span data-stu-id="7be79-116">Explanation</span></span>  
 <span data-ttu-id="7be79-117">MARS(Multiple Active Result Set) 또는 트리거 시나리오에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]는 운영 체제에서 지정하는 미니 버전을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7be79-117">In multiple active result sets (MARS) or trigger scenarios, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses the miniversion specified by the operating system.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="7be79-118">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="7be79-118">User Action</span></span>  
 <span data-ttu-id="7be79-119">동일 트랜잭션의 데이터를 반복해서 업데이트하려 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="7be79-119">Try to avoid repeated updates to the data in the same transaction.</span></span>  
  
  
