---
title: MSSQLSERVER_948 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "948"
helpviewer_keywords:
- 948 (Database Engine error)
ms.assetid: 95c4ad45-a518-4165-a5c4-6e6b932b0570
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e8461069a3fceb7bdca318b82a522f7f51af83d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650033"
---
# <a name="mssqlserver_948"></a><span data-ttu-id="4f6bb-102">MSSQLSERVER_948</span><span class="sxs-lookup"><span data-stu-id="4f6bb-102">MSSQLSERVER_948</span></span>
    
## <a name="details"></a><span data-ttu-id="4f6bb-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="4f6bb-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4f6bb-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="4f6bb-104">Product Name</span></span>|<span data-ttu-id="4f6bb-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="4f6bb-105">SQL Server</span></span>|  
|<span data-ttu-id="4f6bb-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="4f6bb-106">Event ID</span></span>|<span data-ttu-id="4f6bb-107">948</span><span class="sxs-lookup"><span data-stu-id="4f6bb-107">948</span></span>|  
|<span data-ttu-id="4f6bb-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="4f6bb-108">Event Source</span></span>|<span data-ttu-id="4f6bb-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="4f6bb-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="4f6bb-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="4f6bb-110">Component</span></span>|<span data-ttu-id="4f6bb-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="4f6bb-111">SQLEngine</span></span>|  
|<span data-ttu-id="4f6bb-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="4f6bb-112">Symbolic Name</span></span>|<span data-ttu-id="4f6bb-113">해당 없음</span><span class="sxs-lookup"><span data-stu-id="4f6bb-113">NA</span></span>|  
|<span data-ttu-id="4f6bb-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="4f6bb-114">Message Text</span></span>|<span data-ttu-id="4f6bb-115">데이터베이스 '%.\*ls'은(는) 해당 버전이 %d이므로 열 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4f6bb-115">The database '%.\*ls' cannot be opened because it is version %d.</span></span> <span data-ttu-id="4f6bb-116">이 서버는 버전 %d 및 이전 버전을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="4f6bb-116">This server supports version %d and earlier.</span></span> <span data-ttu-id="4f6bb-117">다운그레이드는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4f6bb-117">A downgrade path is not supported.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="4f6bb-118">설명</span><span class="sxs-lookup"><span data-stu-id="4f6bb-118">Explanation</span></span>  
 <span data-ttu-id="4f6bb-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 특정 기능은 데이터베이스 파일의 구조에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4f6bb-119">Certain features in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] affect the structure of the database files.</span></span> <span data-ttu-id="4f6bb-120">다른 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 데이터베이스를 연결하는 경우 파일 형식이 다른 버전의 [!INCLUDE[ssDE](../../includes/ssde-md.md)]과 호환되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f6bb-120">When you attach a database to another instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the file format might not be compatible with a different version of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
 <span data-ttu-id="4f6bb-121">예를 들어 이 오류는 최신 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 vardecimal 스토리지 형식을 사용한 다음 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 서비스 팩 2 이전 버전에서 데이터베이스 파일을 연결하려고 하여 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f6bb-121">For example, this error can be caused by using the vardecimal storage format in a later version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and then trying to attach the database files in a version earlier than [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 2.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="4f6bb-122">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="4f6bb-122">User Action</span></span>  
 <span data-ttu-id="4f6bb-123">원본 서버에서 실행하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 버전을 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="4f6bb-123">Determine the version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is running on the originating server.</span></span> <span data-ttu-id="4f6bb-124">에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 서버를 마우스 오른쪽 단추로 클릭 한 다음 **속성** 을 클릭 하거나 `SELECT @@VERSION` 쿼리 창에서을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f6bb-124">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], either right-click the server and then click **Properties** or type `SELECT @@VERSION` in a query window.</span></span> <span data-ttu-id="4f6bb-125">그런 다음 원래 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]로 데이터베이스를 열어</span><span class="sxs-lookup"><span data-stu-id="4f6bb-125">Open the database by using the original version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="4f6bb-126">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 원래 데이터베이스에 설정되어 있는 기능을 조사한 후</span><span class="sxs-lookup"><span data-stu-id="4f6bb-126">Investigate the features that are enabled on the original database in the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="4f6bb-127">데이터베이스가 연결될 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 작동하도록 이러한 설정을 수정하십시오.</span><span class="sxs-lookup"><span data-stu-id="4f6bb-127">Modify these settings to work with the version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in which the database will be attached.</span></span>  
  
  
