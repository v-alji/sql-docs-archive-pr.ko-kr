---
title: LOCALDB_ERROR_CANNOT_CREATE_INSTANCE_FOLDER | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: 626b73d3-a257-4b45-82fb-c6299faa0001
author: stevestein
ms.author: sstein
ms.openlocfilehash: b127bedb0dc13c0b8b5a238a8ef104ca9a00bd85
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653408"
---
# <a name="localdb_error_cannot_create_instance_folder"></a><span data-ttu-id="6792f-102">LOCALDB_ERROR_CANNOT_CREATE_INSTANCE_FOLDER</span><span class="sxs-lookup"><span data-stu-id="6792f-102">LOCALDB_ERROR_CANNOT_CREATE_INSTANCE_FOLDER</span></span>
    
## <a name="details"></a><span data-ttu-id="6792f-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="6792f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6792f-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="6792f-104">Product Name</span></span>|<span data-ttu-id="6792f-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="6792f-105">SQL Server</span></span>|  
|<span data-ttu-id="6792f-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="6792f-106">Event ID</span></span>|<span data-ttu-id="6792f-107">256</span><span class="sxs-lookup"><span data-stu-id="6792f-107">256</span></span>|  
|<span data-ttu-id="6792f-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="6792f-108">Event Source</span></span>|<span data-ttu-id="6792f-109">SQL Server 로컬 데이터베이스 런타임 12.0</span><span class="sxs-lookup"><span data-stu-id="6792f-109">SQL Server Local Database Runtime 12.0</span></span>|  
|<span data-ttu-id="6792f-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="6792f-110">Component</span></span>|<span data-ttu-id="6792f-111">로컬 데이터베이스 런타임 API</span><span class="sxs-lookup"><span data-stu-id="6792f-111">Local Database Runtime API</span></span>|  
|<span data-ttu-id="6792f-112">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="6792f-112">Message Text</span></span>|<span data-ttu-id="6792f-113">로컬 데이터베이스 인스턴스에 대 한 폴더를 만들 수 없습니다 .%% LOCALAPPDATA%% \ Microsoft\Microsoft SQL Server 로컬 DB\Instances \\<인스턴스 이름 \> 입니다.</span><span class="sxs-lookup"><span data-stu-id="6792f-113">Cannot create folder for the Local Database instance at: %%LOCALAPPDATA%%\Microsoft\Microsoft SQL Server Local DB\Instances\\<instance name\>.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="6792f-114">설명</span><span class="sxs-lookup"><span data-stu-id="6792f-114">Explanation</span></span>  
 <span data-ttu-id="6792f-115">%Userprofile% 아래에 폴더를 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6792f-115">A folder cannot be created under %userprofile%.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6792f-116">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="6792f-116">User Action</span></span>  
  
