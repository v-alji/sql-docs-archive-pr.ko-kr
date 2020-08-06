---
title: MSSQLSERVER_1101 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1101 (Database Engine error)
ms.assetid: d63b67d5-59f5-4f77-904e-5ba67f2dd850
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 631b0ab1466815cbacfd71b4f9fd714fabd0f7b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653964"
---
# <a name="mssqlserver_1101"></a><span data-ttu-id="e899e-102">MSSQLSERVER_1101</span><span class="sxs-lookup"><span data-stu-id="e899e-102">MSSQLSERVER_1101</span></span>
    
## <a name="details"></a><span data-ttu-id="e899e-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="e899e-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e899e-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="e899e-104">Product Name</span></span>|<span data-ttu-id="e899e-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="e899e-105">SQL Server</span></span>|  
|<span data-ttu-id="e899e-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="e899e-106">Event ID</span></span>|<span data-ttu-id="e899e-107">1101</span><span class="sxs-lookup"><span data-stu-id="e899e-107">1101</span></span>|  
|<span data-ttu-id="e899e-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="e899e-108">Event Source</span></span>|<span data-ttu-id="e899e-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="e899e-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="e899e-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="e899e-110">Component</span></span>|<span data-ttu-id="e899e-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="e899e-111">SQLEngine</span></span>|  
|<span data-ttu-id="e899e-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="e899e-112">Symbolic Name</span></span>|<span data-ttu-id="e899e-113">NOALLOCPG</span><span class="sxs-lookup"><span data-stu-id="e899e-113">NOALLOCPG</span></span>|  
|<span data-ttu-id="e899e-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="e899e-114">Message Text</span></span>|<span data-ttu-id="e899e-115">파일 그룹 '%.\*ls'에 디스크 공간이 부족하여 데이터베이스 '%1!s!'에 새 페이지를 할당할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e899e-115">Could not allocate a new page for database '%.\*ls' because of insufficient disk space in filegroup '%.\*ls'.</span></span> <span data-ttu-id="e899e-116">파일 그룹의 개체를 삭제하거나, 파일 그룹에 파일을 추가하거나, 파일 그룹의 기존 파일에 대해 자동 증가를 설정하여 필요한 공간을 만드십시오.</span><span class="sxs-lookup"><span data-stu-id="e899e-116">Create the necessary space by dropping objects in the filegroup, adding additional files to the filegroup, or setting autogrowth on for existing files in the filegroup.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="e899e-117">설명</span><span class="sxs-lookup"><span data-stu-id="e899e-117">Explanation</span></span>  
 <span data-ttu-id="e899e-118">파일 그룹에 사용 가능한 디스크 공간이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e899e-118">No disk space available in a filegroup.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e899e-119">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="e899e-119">User Action</span></span>  
 <span data-ttu-id="e899e-120">다음 동작으로 파일 그룹에 사용 가능한 공간을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e899e-120">The following actions may make space available in the filegroup.</span></span>  
  
-   <span data-ttu-id="e899e-121">AUTOGROW를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e899e-121">Turn on AUTOGROW.</span></span>  
  
-   <span data-ttu-id="e899e-122">파일에 파일 추가</span><span class="sxs-lookup"><span data-stu-id="e899e-122">Add more files to the file group.</span></span>  
  
-   <span data-ttu-id="e899e-123">불필요한 인덱스나 파일 그룹 내의 테이블을 삭제하여 디스크 공간을 확보합니다.</span><span class="sxs-lookup"><span data-stu-id="e899e-123">Free up disk space by dropping unnecessary indexes or tables in the filegroup.</span></span>  
  
  
