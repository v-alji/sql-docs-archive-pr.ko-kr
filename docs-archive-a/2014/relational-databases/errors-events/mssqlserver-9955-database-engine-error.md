---
title: MSSQLSERVER_9955 | Microsoft 문서
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9955 (Database Engine error)
ms.assetid: 77f30570-7790-4747-b372-eac71c036e19
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 56b9f9b4b7923f8973bd7167c3c1bf77e92300c9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650020"
---
# <a name="mssqlserver_9955"></a><span data-ttu-id="e21ec-102">MSSQLSERVER_9955</span><span class="sxs-lookup"><span data-stu-id="e21ec-102">MSSQLSERVER_9955</span></span>
    
## <a name="details"></a><span data-ttu-id="e21ec-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="e21ec-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e21ec-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="e21ec-104">Product Name</span></span>|<span data-ttu-id="e21ec-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="e21ec-105">SQL Server</span></span>|  
|<span data-ttu-id="e21ec-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="e21ec-106">Event ID</span></span>|<span data-ttu-id="e21ec-107">9955</span><span class="sxs-lookup"><span data-stu-id="e21ec-107">9955</span></span>|  
|<span data-ttu-id="e21ec-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="e21ec-108">Event Source</span></span>|<span data-ttu-id="e21ec-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="e21ec-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="e21ec-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="e21ec-110">Component</span></span>|<span data-ttu-id="e21ec-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="e21ec-111">SQLEngine</span></span>|  
|<span data-ttu-id="e21ec-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="e21ec-112">Symbolic Name</span></span>|<span data-ttu-id="e21ec-113">FTXT2_MSSEARCHACCESSDENY</span><span class="sxs-lookup"><span data-stu-id="e21ec-113">FTXT2_MSSEARCHACCESSDENY</span></span>|  
|<span data-ttu-id="e21ec-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="e21ec-114">Message Text</span></span>|<span data-ttu-id="e21ec-115">SQL Server에서 전체 텍스트 필터 데몬(Windows 오류: %d)과 통신하는 명명된 파이프 '%ls'을(를) 만들지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="e21ec-115">SQL Server failed to create named pipe '%ls' to communicate with the full-text filter daemon (Windows error: %d).</span></span> <span data-ttu-id="e21ec-116">필터 데몬 호스트 프로세스에 대한 명명된 파이프가 이미 있거나, 시스템 리소스 공간이 부족하거나, 필터 데몬 계정 그룹에 대한 SID(보안 ID)를 조회하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="e21ec-116">Either a named pipe already exists for a filter daemon host process, the system is low on resources, or the security identification number (SID) lookup for the filter daemon account group failed.</span></span> <span data-ttu-id="e21ec-117">이 오류를 해결하려면 실행 중인 전체 텍스트 필터 데몬 프로세스를 종료하고, 필요한 경우 전체 텍스트 데몬 시작 관리자 서비스 계정을 다시 구성하십시오.</span><span class="sxs-lookup"><span data-stu-id="e21ec-117">To resolve this error, terminate any running full-text filter daemon processes, and if necessary reconfigure the full-text daemon launcher service account.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="e21ec-118">설명</span><span class="sxs-lookup"><span data-stu-id="e21ec-118">Explanation</span></span>  
 <span data-ttu-id="e21ec-119">이 메시지는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 전체 텍스트 필터 데몬과 통신하는 명명된 파이프를 만들지 못한 경우에 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="e21ec-119">This message occurs because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failed to create a named pipe to communicate with the full-text filter daemon.</span></span> <span data-ttu-id="e21ec-120">필터 데몬 호스트 프로세스에 대한 명명된 파이프가 이미 있거나, 시스템 리소스 공간이 부족하거나, 필터 데몬 계정 그룹에 대한 SID(보안 ID)를 조회하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="e21ec-120">Either a named pipe already exists for a filter daemon host process, the system is low on resources, or the security identification number (SID) lookup for the filter daemon account group failed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e21ec-121">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="e21ec-121">User Action</span></span>  
 <span data-ttu-id="e21ec-122">이 오류를 해결하려면 실행 중인 전체 텍스트 필터 데몬 프로세스를 종료하고, 필요한 경우 SQL Server 구성 관리자를 사용하여 전체 텍스트 데몬 호스트 계정을 다시 구성하십시오.</span><span class="sxs-lookup"><span data-stu-id="e21ec-122">To resolve this error, terminate any running full-text filter daemon processes, and if necessary reconfigure the full-text daemon host account by using the SQL Server Configuration Manager.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e21ec-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e21ec-123">See Also</span></span>  
 <span data-ttu-id="e21ec-124">[SQL Server 구성 관리자](../sql-server-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="e21ec-124">[SQL Server Configuration Manager](../sql-server-configuration-manager.md) </span></span>  
 <span data-ttu-id="e21ec-125">[전체 텍스트 필터 데몬 시작 관리자에 대 한 서비스 계정 설정](../search/set-the-service-account-for-the-full-text-filter-daemon-launcher.md) </span><span class="sxs-lookup"><span data-stu-id="e21ec-125">[Set the Service Account for the Full-text Filter Daemon Launcher](../search/set-the-service-account-for-the-full-text-filter-daemon-launcher.md) </span></span>  
 [<span data-ttu-id="e21ec-126">전체 텍스트 검색</span><span class="sxs-lookup"><span data-stu-id="e21ec-126">Full-Text Search</span></span>](../search/full-text-search.md)  
  
  
