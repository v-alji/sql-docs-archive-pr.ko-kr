---
title: MSSQLSERVER_5515 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 5515 (Database Engine error)
ms.assetid: ccd793bc-ba5d-4782-8d72-731fd01fc177
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 74df4571deba596a30a6dd3bd4c186bed03163e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651722"
---
# <a name="mssqlserver_5515"></a><span data-ttu-id="0314a-102">MSSQLSERVER_5515</span><span class="sxs-lookup"><span data-stu-id="0314a-102">MSSQLSERVER_5515</span></span>
    
## <a name="details"></a><span data-ttu-id="0314a-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="0314a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0314a-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="0314a-104">Product Name</span></span>|<span data-ttu-id="0314a-105">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="0314a-105">MSSQLSERVER</span></span>|  
|<span data-ttu-id="0314a-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="0314a-106">Event ID</span></span>|<span data-ttu-id="0314a-107">5515</span><span class="sxs-lookup"><span data-stu-id="0314a-107">5515</span></span>|  
|<span data-ttu-id="0314a-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="0314a-108">Event Source</span></span>|<span data-ttu-id="0314a-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="0314a-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="0314a-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="0314a-110">Component</span></span>|<span data-ttu-id="0314a-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="0314a-111">SQLEngine</span></span>|  
|<span data-ttu-id="0314a-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="0314a-112">Symbolic Name</span></span>|<span data-ttu-id="0314a-113">FS_OPEN_CONTAINER_FAILED</span><span class="sxs-lookup"><span data-stu-id="0314a-113">FS_OPEN_CONTAINER_FAILED</span></span>|  
|<span data-ttu-id="0314a-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="0314a-114">Message Text</span></span>|<span data-ttu-id="0314a-115">FILESTREAM 파일의 컨테이너 디렉터리 ''%.\*ls''을(를) 열 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0314a-115">Container directory ''%.\*ls'' of the FILESTREAM file cannot be opened.</span></span> <span data-ttu-id="0314a-116">운영 체제에서 Windows 상태 코드 0x%x을(를) 반환했습니다.</span><span class="sxs-lookup"><span data-stu-id="0314a-116">The operating system has returned the Windows status code 0x%x.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="0314a-117">설명</span><span class="sxs-lookup"><span data-stu-id="0314a-117">Explanation</span></span>  
 <span data-ttu-id="0314a-118">FILESTREAM 파일에 대해 지정된 컨테이너 디렉터리를 열 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0314a-118">The specified container directory for the FILESTREAM file cannot be opened.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="0314a-119">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="0314a-119">User Action</span></span>  
 <span data-ttu-id="0314a-120">오류의 원인은 해당 Windows 상태 코드를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="0314a-120">For the error cause, see the specific Windows status code.</span></span> <span data-ttu-id="0314a-121">자세한 내용은 [이벤트 및 오류 메시지 지원 센터](https://support.microsoft.com/search?query=events%20and%20errors)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0314a-121">For more information, see the [Events and Errors Message Support Center](https://support.microsoft.com/search?query=events%20and%20errors).</span></span>  
  
  
