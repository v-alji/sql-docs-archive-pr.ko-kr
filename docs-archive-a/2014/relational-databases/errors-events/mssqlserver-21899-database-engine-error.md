---
title: MSSQLSERVER_21899 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 21899 (Database Engine error)
ms.assetid: 32b87a7c-5380-4638-b147-dd78618f6625
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: cb1af04b56685d0e1b5a703b812d08d88909b693
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731640"
---
# <a name="mssqlserver_21899"></a><span data-ttu-id="5682d-102">MSSQLSERVER_21899</span><span class="sxs-lookup"><span data-stu-id="5682d-102">MSSQLSERVER_21899</span></span>
    
## <a name="details"></a><span data-ttu-id="5682d-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="5682d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5682d-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="5682d-104">Product Name</span></span>|<span data-ttu-id="5682d-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="5682d-105">SQL Server</span></span>|  
|<span data-ttu-id="5682d-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="5682d-106">Event ID</span></span>|<span data-ttu-id="5682d-107">21899</span><span class="sxs-lookup"><span data-stu-id="5682d-107">21899</span></span>|  
|<span data-ttu-id="5682d-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="5682d-108">Event Source</span></span>|<span data-ttu-id="5682d-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="5682d-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="5682d-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="5682d-110">Component</span></span>|<span data-ttu-id="5682d-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="5682d-111">SQLEngine</span></span>|  
|<span data-ttu-id="5682d-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="5682d-112">Symbolic Name</span></span>|<span data-ttu-id="5682d-113">SQLErrorNum21899</span><span class="sxs-lookup"><span data-stu-id="5682d-113">SQLErrorNum21899</span></span>|  
|<span data-ttu-id="5682d-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="5682d-114">Message Text</span></span>|<span data-ttu-id="5682d-115">'%d' 오류로 인해 리디렉션된 게시자 '%s'에서 원래 게시자 '%s'의 구독자에 대한 sysserver 항목이 있는지 확인하기 위한 쿼리에 실패했습니다(오류 메시지 '%s').</span><span class="sxs-lookup"><span data-stu-id="5682d-115">The query at the redirected publisher '%s' to determine whether there were sysserver entries for the subscribers of the original publisher '%s' failed with error '%d', error message '%s'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="5682d-116">설명</span><span class="sxs-lookup"><span data-stu-id="5682d-116">Explanation</span></span>  
 <span data-ttu-id="5682d-117">`sp_validate_redirected_publisher`는 원격 서버에 있는 게시자 데이터베이스의 구독 메타데이터 테이블을 쿼리하여 연관된 구독자를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="5682d-117">`sp_validate_redirected_publisher` queries the subscription metadata tables of the publisher database at the remote server to determine its associated subscribers.</span></span> <span data-ttu-id="5682d-118">오류 21899는 이 쿼리에 실패한 경우에 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="5682d-118">Error 21899 is returned if this query fails.</span></span> <span data-ttu-id="5682d-119">유효성 검사 쿼리를 실행하려면 리디렉션된 게시자의 게시된 데이터베이스에 액세스해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5682d-119">The validation query requires access to the published database at the redirected publisher.</span></span> <span data-ttu-id="5682d-120">원래 게시자에 대해 `sp_adddistpublisher`가 호출될 때 지정된 로그인에 리디렉션된 게시자의 게시된 데이터베이스에 액세스할 수 있는 권한이 없으면 오류 21899가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="5682d-120">If the login specified when `sp_adddistpublisher` is called for the original publisher is not authorized to access the published database at the redirected publisher, error 21899 is returned.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5682d-121">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="5682d-121">User Action</span></span>  
 <span data-ttu-id="5682d-122">지정된 오류 메시지를 검토하여 실패 원인을 파악하고 적절한 수정 동작을 수행하십시오.</span><span class="sxs-lookup"><span data-stu-id="5682d-122">Review the cited error message to determine the cause of the failure and take appropriate corrective action</span></span>  
  
  
