---
title: SQL Server, SQL Errors 개체 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQL Errors object
- SQLServer:SQL Errors
ms.assetid: 6e5273ca-29cb-4618-88a2-70b9b8d6cf76
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 11bfb728e79b4fc175fb8a2fe16c9f1662a205ed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729396"
---
# <a name="sql-server-sql-errors-object"></a><span data-ttu-id="0e748-102">SQL Server, SQL Errors 개체</span><span class="sxs-lookup"><span data-stu-id="0e748-102">SQL Server, SQL Errors Object</span></span>
  <span data-ttu-id="0e748-103">Microsoft **의** SQLServer:SQL Errors [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 개체는 **SQL Errors**를 모니터링하는 카운터를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0e748-103">The **SQLServer:SQL Errors** object in Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides counters to monitor **SQL Errors**.</span></span>  
  
 <span data-ttu-id="0e748-104">이 테이블에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **SQL 오류** 카운터에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0e748-104">This table describes the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **SQL Errors** counters.</span></span>  
  
|<span data-ttu-id="0e748-105">SQL Server SQL Errors 카운터</span><span class="sxs-lookup"><span data-stu-id="0e748-105">SQL Server SQL Errors counters</span></span>|<span data-ttu-id="0e748-106">Description</span><span class="sxs-lookup"><span data-stu-id="0e748-106">Description</span></span>|  
|------------------------------------|-----------------|  
|<span data-ttu-id="0e748-107">**Errors/sec**</span><span class="sxs-lookup"><span data-stu-id="0e748-107">**Errors/sec**</span></span>|<span data-ttu-id="0e748-108">초당 오류 개수입니다.</span><span class="sxs-lookup"><span data-stu-id="0e748-108">Number of errors/sec.</span></span>|  
  
 <span data-ttu-id="0e748-109">개체의 각 카운터는 다음 인스턴스를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="0e748-109">Each counter in the object contains the following instances:</span></span>  
  
|<span data-ttu-id="0e748-110">항목</span><span class="sxs-lookup"><span data-stu-id="0e748-110">Item</span></span>|<span data-ttu-id="0e748-111">정의</span><span class="sxs-lookup"><span data-stu-id="0e748-111">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="0e748-112">**_Total**</span><span class="sxs-lookup"><span data-stu-id="0e748-112">**_Total**</span></span>|<span data-ttu-id="0e748-113">모든 오류에 대한 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="0e748-113">Information for all errors.</span></span>|  
|<span data-ttu-id="0e748-114">**DB Offline Errors**</span><span class="sxs-lookup"><span data-stu-id="0e748-114">**DB Offline Errors**</span></span>|<span data-ttu-id="0e748-115">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 현재 데이터베이스를 오프라인 상태로 만드는 심각한 오류를 추적합니다.</span><span class="sxs-lookup"><span data-stu-id="0e748-115">Tracks severe errors that cause [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to take the current database offline.</span></span>|  
|<span data-ttu-id="0e748-116">**Info Errors**</span><span class="sxs-lookup"><span data-stu-id="0e748-116">**Info Errors**</span></span>|<span data-ttu-id="0e748-117">사용자에게 정보를 제공하지만 오류는 발생시키지 않는 오류 메시지 관련 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="0e748-117">Information related to error messages that provide information to users but do not cause errors.</span></span>|  
|<span data-ttu-id="0e748-118">**Kill Connection Errors**</span><span class="sxs-lookup"><span data-stu-id="0e748-118">**Kill Connection Errors**</span></span>|<span data-ttu-id="0e748-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 현재 연결을 해제하게 만드는 심각한 오류를 추적합니다.</span><span class="sxs-lookup"><span data-stu-id="0e748-119">Tracks severe errors that cause [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to kill the current connection.</span></span>|  
|<span data-ttu-id="0e748-120">**User Errors**</span><span class="sxs-lookup"><span data-stu-id="0e748-120">**User Errors**</span></span>|<span data-ttu-id="0e748-121">사용자 오류에 대한 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="0e748-121">Information about user errors.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0e748-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0e748-122">See Also</span></span>  
 [<span data-ttu-id="0e748-123">리소스 사용 모니터링&#40;시스템 모니터&#41;</span><span class="sxs-lookup"><span data-stu-id="0e748-123">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  
