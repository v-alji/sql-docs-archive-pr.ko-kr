---
title: MSSQLSERVER_945 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 945 (Database Engine error)
ms.assetid: ee501d13-0bd9-4627-896c-ed5b1bdb88b3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 51284cdcf48f1bf713a853f9c87457cb5291cc4e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650035"
---
# <a name="mssqlserver_945"></a><span data-ttu-id="82c0f-102">MSSQLSERVER_945</span><span class="sxs-lookup"><span data-stu-id="82c0f-102">MSSQLSERVER_945</span></span>
    
## <a name="details"></a><span data-ttu-id="82c0f-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="82c0f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="82c0f-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="82c0f-104">Product Name</span></span>|<span data-ttu-id="82c0f-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="82c0f-105">SQL Server</span></span>|  
|<span data-ttu-id="82c0f-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="82c0f-106">Event ID</span></span>|<span data-ttu-id="82c0f-107">945</span><span class="sxs-lookup"><span data-stu-id="82c0f-107">945</span></span>|  
|<span data-ttu-id="82c0f-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="82c0f-108">Event Source</span></span>|<span data-ttu-id="82c0f-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="82c0f-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="82c0f-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="82c0f-110">Component</span></span>|<span data-ttu-id="82c0f-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="82c0f-111">SQLEngine</span></span>|  
|<span data-ttu-id="82c0f-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="82c0f-112">Symbolic Name</span></span>|<span data-ttu-id="82c0f-113">DB_IS_SHUTDOWN</span><span class="sxs-lookup"><span data-stu-id="82c0f-113">DB_IS_SHUTDOWN</span></span>|  
|<span data-ttu-id="82c0f-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="82c0f-114">Message Text</span></span>|<span data-ttu-id="82c0f-115">파일에 액세스할 수 없거나 메모리 또는 디스크 공간이 부족하여 데이터베이스 '%.\*ls'을(를) 열 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="82c0f-115">Database '%.\*ls' cannot be opened due to inaccessible files or insufficient memory or disk space.</span></span>  <span data-ttu-id="82c0f-116">자세한 내용은 SQL Server 오류 로그를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="82c0f-116">See the SQL Server error log for details.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="82c0f-117">설명</span><span class="sxs-lookup"><span data-stu-id="82c0f-117">Explanation</span></span>  
 <span data-ttu-id="82c0f-118">파일 또는 기타 리소스가 없어 데이터베이스에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="82c0f-118">The database could not be accessed because files or other resources are missing.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="82c0f-119">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="82c0f-119">User Action</span></span>  
 <span data-ttu-id="82c0f-120">메모리, 디스크 공간 또는 사용 권한 오류에 대한 자세한 내용은 오류 로그를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="82c0f-120">Check the error log for additional information about memory, disk space, or permission failure.</span></span> <span data-ttu-id="82c0f-121">영향을 받는 데이터베이스에 대한 .mdf 및 .ndf 파일의 위치를 확인하고 [!INCLUDE[ssDE](../../includes/ssde-md.md)]에서 사용하는 계정에 해당 .mdf 및 .ndf 파일에 대한 액세스 권한이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="82c0f-121">Confirm the location of the .mdf and .ndf files for the affected database and confirm that the account used by the [!INCLUDE[ssDE](../../includes/ssde-md.md)] has permission to access those files.</span></span> <span data-ttu-id="82c0f-122">문제를 수정한 후에는 ALTER DATABASE를 사용하여 데이터베이스를 ONLINE으로 설정하고 데이터베이스를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="82c0f-122">After correcting the problem, restart the database by using ALTER DATABASE to set it ONLINE.</span></span>  
  
  
