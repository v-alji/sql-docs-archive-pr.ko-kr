---
title: MSSQLSERVER_3271 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3271 (Database Engine error)
ms.assetid: 21b8de4b-6624-4163-9561-1a6cc8fe3d51
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 56bdb5875dbba3fbe5037a308d713170a9b6f9ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650059"
---
# <a name="mssqlserver_3271"></a><span data-ttu-id="e9cb5-102">MSSQLSERVER_3271</span><span class="sxs-lookup"><span data-stu-id="e9cb5-102">MSSQLSERVER_3271</span></span>
    
## <a name="details"></a><span data-ttu-id="e9cb5-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="e9cb5-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e9cb5-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="e9cb5-104">Product Name</span></span>|<span data-ttu-id="e9cb5-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="e9cb5-105">SQL Server</span></span>|  
|<span data-ttu-id="e9cb5-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="e9cb5-106">Event ID</span></span>|<span data-ttu-id="e9cb5-107">3271</span><span class="sxs-lookup"><span data-stu-id="e9cb5-107">3271</span></span>|  
|<span data-ttu-id="e9cb5-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="e9cb5-108">Event Source</span></span>|<span data-ttu-id="e9cb5-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="e9cb5-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="e9cb5-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="e9cb5-110">Component</span></span>|<span data-ttu-id="e9cb5-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="e9cb5-111">SQLEngine</span></span>|  
|<span data-ttu-id="e9cb5-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="e9cb5-112">Symbolic Name</span></span>|<span data-ttu-id="e9cb5-113">DMPIO_IO_ERROR</span><span class="sxs-lookup"><span data-stu-id="e9cb5-113">DMPIO_IO_ERROR</span></span>|  
|<span data-ttu-id="e9cb5-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="e9cb5-114">Message Text</span></span>|<span data-ttu-id="e9cb5-115">파일 "%ls"에서 복구할 수 없는 I/O 오류가 발생했습니다: %ls.</span><span class="sxs-lookup"><span data-stu-id="e9cb5-115">A nonrecoverable I/O error occurred on file "%ls:" %ls.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="e9cb5-116">설명</span><span class="sxs-lookup"><span data-stu-id="e9cb5-116">Explanation</span></span>  
 <span data-ttu-id="e9cb5-117">이 오류는 백업 또는 복원 작업을 위한 I/O를 수행하는 동안 운영 체제에서 오류가 발생할 때 일어나는 일반적인 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="e9cb5-117">This is a general error that occurs when the operating system raises an error while performing I/O during a backup or restore operation.</span></span> <span data-ttu-id="e9cb5-118">대부분의 경우 원인은 백업 미디어가 꽉 찼기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="e9cb5-118">In most situations the cause is simply that the backup medium is full.</span></span>  
  
 <span data-ttu-id="e9cb5-119">이 오류에는 디스크가 꽉 찼음을 나타내는 운영 체제 텍스트가 추가로 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e9cb5-119">The error may include additional text from the operating system indicating that the disk is full.</span></span> <span data-ttu-id="e9cb5-120">타사의 백업 소프트웨어를 사용하여 백업 또는 복원 작업을 수행하는 경우 백업에 실패했음을 나타내는 메시지가 추가로 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e9cb5-120">When performing a backup or restore operation with third-party backup software an additional message may occur indicating that the backup failed.</span></span> <span data-ttu-id="e9cb5-121">이 메시지는 다음 텍스트와 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="e9cb5-121">The message may look similar to the following text:</span></span>  
  
```  
"2005-08-02 16:05:16.04 spid55 Error: 18210, Severity: 16, State: 1.  
 2005-08-02 16:05:16.04 spid55 BackupVirtualDeviceFile  
::RequestDurableMedia: Flush failure on backup device 'VDINULL'.   
Operating system error 995(The I/O operation has been aborted because   
of either a thread exit or an application request.)."  
```  
  
 <span data-ttu-id="e9cb5-122">이 텍스트는 백업 소프트웨어가 백업 또는 복원 작업의 종료를 요청했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e9cb5-122">This is an indication that the backup software requested a termination of the backup or restore operation.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e9cb5-123">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="e9cb5-123">User Action</span></span>  
 <span data-ttu-id="e9cb5-124">다음 태스크를 적절하게 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="e9cb5-124">Perform the following tasks as appropriate:</span></span>  
  
-   <span data-ttu-id="e9cb5-125">오류의 원인을 파악하려면 이 오류 이전에 나오는 기본 시스템 오류 메시지 및 SQL Server 오류 메시지를 검토하십시오.</span><span class="sxs-lookup"><span data-stu-id="e9cb5-125">Review the underlying system error messages and SQL Server error messages preceding this one to identify the cause of the failure.</span></span>  
  
-   <span data-ttu-id="e9cb5-126">백업 및 복원 미디어에 충분한 공간이 있는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="e9cb5-126">Ensure that the backup and restore medium has sufficient space.</span></span>  
  
-   <span data-ttu-id="e9cb5-127">타사 백업 및 복원 소프트웨어에서 발생한 오류를 수정하십시오.</span><span class="sxs-lookup"><span data-stu-id="e9cb5-127">Correct any errors raised by third-party backup and restore software.</span></span>  
  
  
