---
title: LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: c178a308-8d99-47fc-8a49-5a480dc592f6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 32ae8ebe102008d08a6059328ed57cd118ece019
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660597"
---
# <a name="localdb_error_instance_folder_path_too_long"></a><span data-ttu-id="3e66e-102">LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG</span><span class="sxs-lookup"><span data-stu-id="3e66e-102">LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG</span></span>
    
## <a name="details"></a><span data-ttu-id="3e66e-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="3e66e-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3e66e-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="3e66e-104">Product Name</span></span>|<span data-ttu-id="3e66e-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="3e66e-105">SQL Server</span></span>|  
|<span data-ttu-id="3e66e-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="3e66e-106">Event ID</span></span>|<span data-ttu-id="3e66e-107">260</span><span class="sxs-lookup"><span data-stu-id="3e66e-107">260</span></span>|  
|<span data-ttu-id="3e66e-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="3e66e-108">Event Source</span></span>|<span data-ttu-id="3e66e-109">SQL Server 로컬 데이터베이스 런타임 12.0</span><span class="sxs-lookup"><span data-stu-id="3e66e-109">SQL Server Local Database Runtime 12.0</span></span>|  
|<span data-ttu-id="3e66e-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="3e66e-110">Component</span></span>|<span data-ttu-id="3e66e-111">로컬 데이터베이스 런타임 API</span><span class="sxs-lookup"><span data-stu-id="3e66e-111">Local Database Runtime API</span></span>|  
|<span data-ttu-id="3e66e-112">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="3e66e-112">Message Text</span></span>|<span data-ttu-id="3e66e-113">로컬 데이터베이스 인스턴스 폴더의 전체 경로 길이가 MAX_PATH보다 깁니다.</span><span class="sxs-lookup"><span data-stu-id="3e66e-113">The full path length of the Local Database instance folder is longer than MAX_PATH.</span></span> <span data-ttu-id="3e66e-114">인스턴스는 인스턴스 이름<%% LOCALAPPDATA%% \ Microsoft\Microsoft SQL Server 로컬 DB\Instances 폴더에 저장 해야 합니다. \\ \></span><span class="sxs-lookup"><span data-stu-id="3e66e-114">The instance must be stored in folder: %%LOCALAPPDATA%%\Microsoft\Microsoft SQL Server Local DB\Instances\\<instance name\>.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="3e66e-115">설명</span><span class="sxs-lookup"><span data-stu-id="3e66e-115">Explanation</span></span>  
 <span data-ttu-id="3e66e-116">인스턴스를 저장할 경로가 MAX_PATH보다 깁니다.</span><span class="sxs-lookup"><span data-stu-id="3e66e-116">The path where the instance should be stored is longer than MAX_PATH.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="3e66e-117">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="3e66e-117">User Action</span></span>  
 <span data-ttu-id="3e66e-118">MAX_PATH보다 길지 않은 새 경로를 만드십시오.</span><span class="sxs-lookup"><span data-stu-id="3e66e-118">Create a new path that is shorter than MAX_PATH.</span></span>  
  
  
