---
title: filestream access level 서버 구성 옵션 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], access level
- filestream access level
ms.assetid: b88f6ff2-795e-4730-bfb8-dbc6a958f2ad
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: dfa43b8e6e1762e87dd9c2abbdf7a583963e196e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660713"
---
# <a name="filestream-access-level-server-configuration-option"></a><span data-ttu-id="60792-102">filestream access level 서버 구성 옵션</span><span class="sxs-lookup"><span data-stu-id="60792-102">filestream access level Server Configuration Option</span></span>
  <span data-ttu-id="60792-103">filestream_access_level 옵션을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 이 인스턴스에 대한 FILESTREAM 액세스 수준을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60792-103">Use the filestream_access_level option to change the FILESTREAM access level for this instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="60792-104">이 옵션이 적용되려면 먼저 FILESTREAM에 대한 Windows 관리 설정을 사용하도록 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="60792-104">Before this option has any effect, the Windows administration settings for FILESTREAM must be enabled.</span></span> <span data-ttu-id="60792-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 시 또는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자를 사용하여 이러한 설정을 사용하도록 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60792-105">You can enable these settings when you install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
|<span data-ttu-id="60792-106">값</span><span class="sxs-lookup"><span data-stu-id="60792-106">Value</span></span>|<span data-ttu-id="60792-107">정의</span><span class="sxs-lookup"><span data-stu-id="60792-107">Definition</span></span>|  
|-----------|----------------|  
|<span data-ttu-id="60792-108">0</span><span class="sxs-lookup"><span data-stu-id="60792-108">0</span></span>|<span data-ttu-id="60792-109">이 인스턴스에 대한 FILESTREAM 지원을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="60792-109">Disables FILESTREAM support for this instance.</span></span>|  
|<span data-ttu-id="60792-110">1</span><span class="sxs-lookup"><span data-stu-id="60792-110">1</span></span>|<span data-ttu-id="60792-111">[!INCLUDE[tsql](../../includes/tsql-md.md)] 액세스에 FILESTREAM을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="60792-111">Enables FILESTREAM for [!INCLUDE[tsql](../../includes/tsql-md.md)] access.</span></span>|  
|<span data-ttu-id="60792-112">2</span><span class="sxs-lookup"><span data-stu-id="60792-112">2</span></span>|<span data-ttu-id="60792-113">[!INCLUDE[tsql](../../includes/tsql-md.md)] 및 Win32 스트리밍 액세스에 FILESTREAM을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="60792-113">Enables FILESTREAM for [!INCLUDE[tsql](../../includes/tsql-md.md)] and Win32 streaming access.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="60792-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="60792-114">See Also</span></span>  
 <span data-ttu-id="60792-115">[데이터베이스 엔진 구성 - Filestream](../../sql-server/install/database-engine-configuration-filestream.md) </span><span class="sxs-lookup"><span data-stu-id="60792-115">[Database Engine Configuration - Filestream](../../sql-server/install/database-engine-configuration-filestream.md) </span></span>  
 [<span data-ttu-id="60792-116">Enable and Configure FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="60792-116">Enable and Configure FILESTREAM</span></span>](../../relational-databases/blob/enable-and-configure-filestream.md)  
  
  
