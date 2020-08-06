---
title: MSSQLSERVER_9790 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9790 (Database Engine error)
ms.assetid: 83fd379f-5deb-4f97-8cb4-282e3d3fed94
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6d6d065d4a0e841da3b5ecb84f902df17dcfd60c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650030"
---
# <a name="mssqlserver_9790"></a><span data-ttu-id="ad72e-102">MSSQLSERVER_9790</span><span class="sxs-lookup"><span data-stu-id="ad72e-102">MSSQLSERVER_9790</span></span>
    
## <a name="details"></a><span data-ttu-id="ad72e-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="ad72e-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ad72e-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="ad72e-104">Product Name</span></span>|<span data-ttu-id="ad72e-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="ad72e-105">SQL Server</span></span>|  
|<span data-ttu-id="ad72e-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="ad72e-106">Event ID</span></span>|<span data-ttu-id="ad72e-107">9790</span><span class="sxs-lookup"><span data-stu-id="ad72e-107">9790</span></span>|  
|<span data-ttu-id="ad72e-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="ad72e-108">Event Source</span></span>|<span data-ttu-id="ad72e-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="ad72e-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="ad72e-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="ad72e-110">Component</span></span>|<span data-ttu-id="ad72e-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="ad72e-111">SQLEngine</span></span>|  
|<span data-ttu-id="ad72e-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="ad72e-112">Symbolic Name</span></span>|<span data-ttu-id="ad72e-113">SB3_XMIT_ERROR_ENTRANCE_BROKER_SINGLE_USER</span><span class="sxs-lookup"><span data-stu-id="ad72e-113">SB3_XMIT_ERROR_ENTRANCE_BROKER_SINGLE_USER</span></span>|  
|<span data-ttu-id="ad72e-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="ad72e-114">Message Text</span></span>|<span data-ttu-id="ad72e-115">들어오는 메시지를 라우팅할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ad72e-115">Unable to route the incoming message.</span></span> <span data-ttu-id="ad72e-116">라우팅 정보를 포함하는 시스템 데이터베이스 MSDB가 단일 사용자 모드입니다.</span><span class="sxs-lookup"><span data-stu-id="ad72e-116">The system database MSDB containing routing information is in SINGLE USER mode.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ad72e-117">설명</span><span class="sxs-lookup"><span data-stu-id="ad72e-117">Explanation</span></span>  
 <span data-ttu-id="ad72e-118">MSDB 데이터베이스가 단일 사용자 모드에 있었기 때문에 네트워크를 통해 수신한 메시지를 분류하려고 하는 동안 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="ad72e-118">An error occurred while trying to classify a message received off the wire because the MSDB database was in Single User mode.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ad72e-119">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="ad72e-119">User Action</span></span>  
 <span data-ttu-id="ad72e-120">ALTER DATABASE 명령을 사용하여 MSDB를 다중 사용자 모드로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="ad72e-120">Change MSDB to be in MULTI USER mode with the ALTER DATABASE command.</span></span>  
  
  
