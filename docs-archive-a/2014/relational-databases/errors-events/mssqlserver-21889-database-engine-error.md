---
title: MSSQLSERVER_21889 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 21889 (Database Engine error)
ms.assetid: ae199540-7986-4cc2-b782-cd22793236d3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c152a542550d7b81af880545f526037baeb4644e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734096"
---
# <a name="mssqlserver_21889"></a><span data-ttu-id="64c82-102">MSSQLSERVER_21889</span><span class="sxs-lookup"><span data-stu-id="64c82-102">MSSQLSERVER_21889</span></span>
    
## <a name="details"></a><span data-ttu-id="64c82-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="64c82-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="64c82-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="64c82-104">Product Name</span></span>|<span data-ttu-id="64c82-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="64c82-105">SQL Server</span></span>|  
|<span data-ttu-id="64c82-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="64c82-106">Event ID</span></span>|<span data-ttu-id="64c82-107">21889</span><span class="sxs-lookup"><span data-stu-id="64c82-107">21889</span></span>|  
|<span data-ttu-id="64c82-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="64c82-108">Event Source</span></span>|<span data-ttu-id="64c82-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="64c82-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="64c82-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="64c82-110">Component</span></span>|<span data-ttu-id="64c82-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="64c82-111">SQLEngine</span></span>|  
|<span data-ttu-id="64c82-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="64c82-112">Symbolic Name</span></span>|<span data-ttu-id="64c82-113">SQLErrorNum21889</span><span class="sxs-lookup"><span data-stu-id="64c82-113">SQLErrorNum21889</span></span>|  
|<span data-ttu-id="64c82-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="64c82-114">Message Text</span></span>|<span data-ttu-id="64c82-115">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스 '%s'이(가) 복제 게시자가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="64c82-115">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance '%s' is not a replication publisher.</span></span> <span data-ttu-id="64c82-116">이 인스턴스에서 게시 데이터베이스 '%s'을(를) 호스팅하도록 설정하려면 배포자가 '%s'인 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스 '%s'에서 `sp_adddistributor`를 실행하십시오.</span><span class="sxs-lookup"><span data-stu-id="64c82-116">Run `sp_adddistributor` on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance '%s' with distributor '%s' in order to enable the instance to host the publishing database '%s'.</span></span> <span data-ttu-id="64c82-117">이때 원래 게시자에 사용된 것과 동일한 로그인 및 암호를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="64c82-117">Make certain to specify the same login and password as that used for the original publisher.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="64c82-118">설명</span><span class="sxs-lookup"><span data-stu-id="64c82-118">Explanation</span></span>  
 <span data-ttu-id="64c82-119">게시자 데이터베이스를 호스팅하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스가 복제 게시자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="64c82-119">In order to host the publisher database, the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must be a replication publisher.</span></span> <span data-ttu-id="64c82-120">`sp_validate_redirected_publisher`는 원격 서버에서 `sp_helpdistributor`를 호출하여 서버가 복제 게시자인지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="64c82-120">`sp_validate_redirected_publisher` calls `sp_helpdistributor` at the remote server to determine whether the server is a replication publisher.</span></span> <span data-ttu-id="64c82-121">이 오류는 `sp_helpdistributor` 저장 프로시저를 실행할 때 대상 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스가 복제 게시자가 아닌 것으로 나타난 경우에 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="64c82-121">This error is returned when execution of the stored procedure `sp_helpdistributor` indicates that the target instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is not a replication publisher.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="64c82-122">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="64c82-122">User Action</span></span>  
 <span data-ttu-id="64c82-123">게시자 데이터베이스를 호스팅하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에서 `sp_adddistributor`를 실행하십시오.</span><span class="sxs-lookup"><span data-stu-id="64c82-123">Execute `sp_adddistributor` at the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that hosts the publisher database.</span></span> <span data-ttu-id="64c82-124">올바른 배포자를 지정하여 `sp_adddistributor`를 실행하십시오.</span><span class="sxs-lookup"><span data-stu-id="64c82-124">When running `sp_adddistributor`, specify the correct distributor.</span></span> <span data-ttu-id="64c82-125">*@password* `sp_adddistributor` 처음에 배포자에서를 실행할 때 사용 된 매개 변수와 동일한 값을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="64c82-125">Use the same value for the *@password* parameter as that used when `sp_adddistributor` was initially run at the distributor.</span></span>  
  
  
