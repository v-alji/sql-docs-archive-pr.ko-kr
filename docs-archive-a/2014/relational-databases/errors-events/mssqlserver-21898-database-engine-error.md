---
title: MSSQLSERVER_21898 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 21898 (Database Engine error)
ms.assetid: 02405b21-3d4e-4c2d-b4b3-d7b1ec05edb4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 78ce7eacf7f026bf9977af2c367b954a3639b357
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731644"
---
# <a name="mssqlserver_21898"></a><span data-ttu-id="86fbe-102">MSSQLSERVER_21898</span><span class="sxs-lookup"><span data-stu-id="86fbe-102">MSSQLSERVER_21898</span></span>
    
## <a name="details"></a><span data-ttu-id="86fbe-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="86fbe-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="86fbe-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="86fbe-104">Product Name</span></span>|<span data-ttu-id="86fbe-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="86fbe-105">SQL Server</span></span>|  
|<span data-ttu-id="86fbe-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="86fbe-106">Event ID</span></span>|<span data-ttu-id="86fbe-107">21898</span><span class="sxs-lookup"><span data-stu-id="86fbe-107">21898</span></span>|  
|<span data-ttu-id="86fbe-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="86fbe-108">Event Source</span></span>|<span data-ttu-id="86fbe-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="86fbe-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="86fbe-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="86fbe-110">Component</span></span>|<span data-ttu-id="86fbe-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="86fbe-111">SQLEngine</span></span>|  
|<span data-ttu-id="86fbe-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="86fbe-112">Symbolic Name</span></span>|<span data-ttu-id="86fbe-113">SQLErrorNum21898</span><span class="sxs-lookup"><span data-stu-id="86fbe-113">SQLErrorNum21898</span></span>|  
|<span data-ttu-id="86fbe-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="86fbe-114">Message Text</span></span>|<span data-ttu-id="86fbe-115">게시자 '%s'이(가) 배포 데이터베이스 '%s'을(를) 사용하며, 게시 데이터베이스 '%s'을(를) 호스팅하는 데 필요한 '%s'이(가) 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="86fbe-115">The publisher '%s' uses distribution database '%s' and not '%s' which is required in order to host the publishing database '%s'.</span></span> <span data-ttu-id="86fbe-116">배포자 '%s'에서 `sp_changedistpublisher`를 실행하여 게시자가 사용하는 배포 데이터베이스를 '%s'(으)로 변경하십시오.</span><span class="sxs-lookup"><span data-stu-id="86fbe-116">Run `sp_changedistpublisher` at distributor '%s' to change the distribution database used by the publisher to '%s'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="86fbe-117">설명</span><span class="sxs-lookup"><span data-stu-id="86fbe-117">Explanation</span></span>  
 <span data-ttu-id="86fbe-118">`sp_validate_redirected_publisher`는 로컬 배포자에서 msdb.dbo.MSdistpublishers를 쿼리하여 새 게시자가 사용하는 배포 데이터베이스가 원래 게시자에 사용된 배포 데이터베이스와 동일한지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="86fbe-118">`sp_validate_redirected_publisher` queries msdb.dbo.MSdistpublishers at the local distributor to verify that the distribution database used by the new publisher is the same as the distribution database used by the original publisher.</span></span> <span data-ttu-id="86fbe-119">이 오류는 이 두 데이터베이스가 서로 달라 게시자가 게시자 데이터베이스에 대한 적합한 호스트가 될 수 없는 경우에 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="86fbe-119">This error is returned when these databases are different, making the publisher an unsuitable host for the publisher database.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="86fbe-120">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="86fbe-120">User Action</span></span>  
 <span data-ttu-id="86fbe-121">`sp_changedistpublisher` 저장 프로시저를 실행하여 새 게시자의 배포 데이터베이스를 원래 게시자에 사용된 배포 데이터베이스로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="86fbe-121">Execute stored procedure `sp_changedistpublisher` to change the distribution database for the new publisher to that used by the original publisher.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="86fbe-122">배포자에서 게시자에 대해 `sp_changedistpublisher`를 실행할 때 잘못된 배포 데이터베이스를 입력한 경우에는 `sp_adddistpublisher`를 실행하면 문제가 해결됩니다.</span><span class="sxs-lookup"><span data-stu-id="86fbe-122">Running `sp_changedistpublisher` will address the problem if the wrong distribution database was entered when `sp_adddistpublisher` was run at the distributor for the publisher.</span></span> <span data-ttu-id="86fbe-123">그러나 원격 게시자에 식별된 배포 데이터베이스를 사용하는 다른 게시 데이터베이스의 기존 게시가 있는 경우에는 이와 같은 변경이 적절하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="86fbe-123">However, if the remote publisher has existing publications from another publishing database that make use of the identified distribution database, this change is not appropriate.</span></span> <span data-ttu-id="86fbe-124">명명된 배포 데이터베이스를 사용하는 복제를 체계적으로 제거한 다음, 원래 게시자의 배포 데이터베이스를 사용하여 데이터베이스를 다시 설정해야만 새 게시자가 적합한 호스트로 작동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86fbe-124">Replication using the named distribution database needs to be systematically removed and then reestablished using the original publisher's distribution database in order for the new publisher to function as a suitable host.</span></span>  
  
  
