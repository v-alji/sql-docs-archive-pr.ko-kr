---
title: MSSQLSERVER_21893 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 21893 (Database Engine error)
ms.assetid: 1ab1195a-fe2a-4e06-b871-b177b6bea1fe
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 92479d7727ac2300d6a60d02492667d99a69b022
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653433"
---
# <a name="mssqlserver_21893"></a><span data-ttu-id="d275f-102">MSSQLSERVER_21893</span><span class="sxs-lookup"><span data-stu-id="d275f-102">MSSQLSERVER_21893</span></span>
    
## <a name="details"></a><span data-ttu-id="d275f-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="d275f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d275f-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="d275f-104">Product Name</span></span>|<span data-ttu-id="d275f-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="d275f-105">SQL Server</span></span>|  
|<span data-ttu-id="d275f-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="d275f-106">Event ID</span></span>|<span data-ttu-id="d275f-107">21893</span><span class="sxs-lookup"><span data-stu-id="d275f-107">21893</span></span>|  
|<span data-ttu-id="d275f-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="d275f-108">Event Source</span></span>|<span data-ttu-id="d275f-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="d275f-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="d275f-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="d275f-110">Component</span></span>|<span data-ttu-id="d275f-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="d275f-111">SQLEngine</span></span>|  
|<span data-ttu-id="d275f-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="d275f-112">Symbolic Name</span></span>|<span data-ttu-id="d275f-113">SQLErrorNum21893</span><span class="sxs-lookup"><span data-stu-id="d275f-113">SQLErrorNum21893</span></span>|  
|<span data-ttu-id="d275f-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="d275f-114">Message Text</span></span>|<span data-ttu-id="d275f-115">원래 게시자 '%s'의 구독자(%s)가 리디렉션된 게시자 '%s'에 원격 서버로 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d275f-115">The subscribers ( %s ) of original publisher '%s' do not appear as remote servers at redirected publisher '%s'.</span></span> <span data-ttu-id="d275f-116">`sp_addlinkedserver`리디렉션된 게시자에서를 실행 하 여 이러한 구독자를 원격 서버로 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="d275f-116">Run `sp_addlinkedserver` at the redirected publisher to add these subscribers as remote servers .</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d275f-117">설명</span><span class="sxs-lookup"><span data-stu-id="d275f-117">Explanation</span></span>  
 <span data-ttu-id="d275f-118">`sp_validate_redirected_publisher`는 원격 서버에 있는 게시자 데이터베이스의 구독 메타데이터 테이블을 사용하여 연관된 구독자를 식별하고 이러한 구독자에 대해 master.dbo.sysservers에 연관된 항목이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d275f-118">`sp_validate_redirected_publisher` uses the subscription metadata tables of the publisher database at the remote server to identify its associated subscribers and verifies that there are associated entries in master.dbo.sysservers for the subscribers.</span></span> <span data-ttu-id="d275f-119">이 오류는 식별된 구독자 중 하나라도 없는 경우에 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="d275f-119">This error is returned if any of the identified subscribers are not present.</span></span>  
  
 <span data-ttu-id="d275f-120">이는 오류로 간주되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d275f-120">This error is not considered a fatal error.</span></span> <span data-ttu-id="d275f-121">이 오류가 발생한 에이전트에서는 이 오류를 정보로 기록하지만 에이전트가 종료되지는 않습니다. 이는 새 게시자에 적절한 구독자 항목이 없더라도 복제에 주는 영향이 적기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="d275f-121">Agents encountering this error will log the error as informational but will not terminate, since a failure to have appropriate subscriber entries at the new publisher has limited impact on replication.</span></span> <span data-ttu-id="d275f-122">sysservers에 구독자에 대한 적절한 항목이 없으면 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 통해 일부 구독 관리 작업을 수행할 경우 작업이 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d275f-122">Without an appropriate entry for a subscriber in sysservers, some subscription management activities may fail when executed through [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="d275f-123">하지만 관리 저장 프로시저를 명시적으로 실행하여 동일한 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d275f-123">However, these same activities can be successfully performed by executing the management stored procedures explicitly.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d275f-124">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="d275f-124">User Action</span></span>  
 <span data-ttu-id="d275f-125">리디렉션된 게시자에서 식별된 각 구독자에 대해 `sp_addlinkedserver`를 실행하여 각각을 원격 서버로 추가한 다음</span><span class="sxs-lookup"><span data-stu-id="d275f-125">Run `sp_addlinkedserver` at the redirected publisher for each of the identified subscribers to add them as remote servers.</span></span> <span data-ttu-id="d275f-126">`sp_serveroption`을 실행하여 서버에 대해 구독자 비트를 설정하십시오.</span><span class="sxs-lookup"><span data-stu-id="d275f-126">Then, run `sp_serveroption` to set the subscriber bit for the server.</span></span>  
  
  
