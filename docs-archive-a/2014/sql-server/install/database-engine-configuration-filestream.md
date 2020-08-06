---
title: 데이터베이스 엔진 구성-Filestream | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], about FILESTREAM
ms.assetid: 641a10a1-ae52-4d26-8f1c-a032a4aeff02
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: ab12b507246a3e13ac59be213813604d531d9a28
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735907"
---
# <a name="database-engine-configuration---filestream"></a><span data-ttu-id="4a87a-102">데이터베이스 엔진 구성 - Filestream</span><span class="sxs-lookup"><span data-stu-id="4a87a-102">Database Engine Configuration - Filestream</span></span>
  <span data-ttu-id="4a87a-103">이 페이지를 사용하여 이 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 설치에 대해 FILESTREAM을 사용하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a87a-103">Use this page to enable FILESTREAM for this installation of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="4a87a-104">FILESTREAM은 `varbinary(max)` BLOB(Binary Large Object) 데이터를 파일 시스템의 파일로 저장하여 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]을 NTFS 파일 시스템과 통합합니다.</span><span class="sxs-lookup"><span data-stu-id="4a87a-104">FILESTREAM integrates the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] with an NTFS file system by storing `varbinary(max)` binary large object (BLOB) data as files on the file system.</span></span> [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="4a87a-105">문은 FILESTREAM 데이터를 삽입, 업데이트, 쿼리, 검색 및 백업할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a87a-105">statements can insert, update, query, search, and back up FILESTREAM data.</span></span> <span data-ttu-id="4a87a-106">Win32 파일 시스템 인터페이스에서는 데이터에 대한 스트리밍 액세스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4a87a-106">Win32 file system interfaces provide streaming access to the data.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="4a87a-107">UI 요소 목록</span><span class="sxs-lookup"><span data-stu-id="4a87a-107">UI element list</span></span>  
 <span data-ttu-id="4a87a-108">**Transact-SQL 액세스에 FILESTREAM 사용**</span><span class="sxs-lookup"><span data-stu-id="4a87a-108">**Enable FILESTREAM for Transact-SQL access**</span></span>  
 <span data-ttu-id="4a87a-109">[!INCLUDE[tsql](../../includes/tsql-md.md)] 액세스에 FILESTREAM을 사용하도록 설정하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4a87a-109">Select to enable FILESTREAM for [!INCLUDE[tsql](../../includes/tsql-md.md)] access.</span></span> <span data-ttu-id="4a87a-110">다른 컨트롤 옵션을 사용하려면 먼저 이 컨트롤을 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4a87a-110">This control must be checked before the other control options will be available.</span></span>  
  
 <span data-ttu-id="4a87a-111">**파일 I/O 스트리밍 액세스에 FILESTREAM 사용**</span><span class="sxs-lookup"><span data-stu-id="4a87a-111">**Enable FILESTREAM for file I/O streaming access**</span></span>  
 <span data-ttu-id="4a87a-112">Win32 스트리밍 액세스에 FILESTREAM을 사용하도록 설정하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4a87a-112">Select to enable Win32 streaming access for FILESTREAM.</span></span>  
  
 <span data-ttu-id="4a87a-113">**Windows 공유 이름**</span><span class="sxs-lookup"><span data-stu-id="4a87a-113">**Windows share name**</span></span>  
 <span data-ttu-id="4a87a-114">FILESTREAM 데이터가 저장될 Windows 공유의 이름을 입력하려면 이 컨트롤을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4a87a-114">Use this control to enter the name of the Windows share in which the FILESTREAM data will be stored.</span></span>  
  
 <span data-ttu-id="4a87a-115">**원격 클라이언트가 FILESTREAM 데이터에 대한 스트리밍 액세스를 가질 수 있도록 허용**</span><span class="sxs-lookup"><span data-stu-id="4a87a-115">**Allow remote clients to have streaming access to FILESTREAM data**</span></span>  
 <span data-ttu-id="4a87a-116">원격 클라이언트가 이 서버의 이 FILESTREAM 데이터에 액세스할 수 있도록 허용하려면 이 컨트롤을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4a87a-116">Select this control to allow remote clients to access this FILESTREAM data on this server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a87a-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4a87a-117">See Also</span></span>  
 <span data-ttu-id="4a87a-118">[FILESTREAM 사용 및 구성](../../relational-databases/blob/enable-and-configure-filestream.md) </span><span class="sxs-lookup"><span data-stu-id="4a87a-118">[Enable and Configure FILESTREAM](../../relational-databases/blob/enable-and-configure-filestream.md) </span></span>  
 [<span data-ttu-id="4a87a-119">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="4a87a-119">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
