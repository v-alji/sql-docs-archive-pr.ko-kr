---
title: 데이터베이스 속성(변경 내용 추적 페이지) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.databaseproperties.changetracking.f1
ms.assetid: 9b929640-bc62-449b-9b06-b5a77b8cf372
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4107f81ef4cdf19df60d4a70d8e79007f2c9270c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734136"
---
# <a name="database-properties-changetracking-page"></a><span data-ttu-id="0feb6-102">데이터베이스 속성(변경 내용 추적 페이지)</span><span class="sxs-lookup"><span data-stu-id="0feb6-102">Database Properties (ChangeTracking Page)</span></span>
  <span data-ttu-id="0feb6-103">이 페이지를 사용하여 선택한 데이터베이스의 변경 내용 추적 설정을 확인하거나 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0feb6-103">Use this page to view or modify change tracking settings for the selected database.</span></span> <span data-ttu-id="0feb6-104">이 페이지에서 사용할 수 있는 옵션에 대한 자세한 내용은 [변경 내용 추적 설정 및 해제&#40;SQL Server&#41;](../track-changes/enable-and-disable-change-tracking-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0feb6-104">For more information about the options available on this page, see [Enable and Disable Change Tracking &#40;SQL Server&#41;](../track-changes/enable-and-disable-change-tracking-sql-server.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="0feb6-105">옵션</span><span class="sxs-lookup"><span data-stu-id="0feb6-105">Options</span></span>  
 <span data-ttu-id="0feb6-106">**변경 내용 추적**</span><span class="sxs-lookup"><span data-stu-id="0feb6-106">**Change Tracking**</span></span>  
 <span data-ttu-id="0feb6-107">데이터베이스에 대해 변경 내용 추적을 설정하거나 해제하는 데 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0feb6-107">Use to enable or disable change tracking for the database.</span></span>  
  
 <span data-ttu-id="0feb6-108">변경 내용 추적을 설정하려면 데이터베이스를 수정할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0feb6-108">To enable change tracking, you must have permission to modify the database.</span></span>  
  
 <span data-ttu-id="0feb6-109">값을 **True** 로 설정하면 개별 테이블에 변경 내용 추적을 사용하는 데이터베이스 옵션이 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="0feb6-109">Setting the value to **True** sets a database option that allows change tracking to be enabled on individual tables.</span></span>  
  
 <span data-ttu-id="0feb6-110">[ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql)를 사용하여 변경 내용 추적을 구성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0feb6-110">You can also configure change tracking by using [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
 <span data-ttu-id="0feb6-111">**보존 기간**</span><span class="sxs-lookup"><span data-stu-id="0feb6-111">**Retention Period**</span></span>  
 <span data-ttu-id="0feb6-112">데이터베이스에 변경 내용 추적 정보를 보존하는 최소 기간을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0feb6-112">Specifies the minimum period for keeping change track information in the database.</span></span> <span data-ttu-id="0feb6-113">데이터는 **자동 정리**값이 **True**인 경우에만 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="0feb6-113">Data is removed only if the **Auto Clean-Up**value is **True**.</span></span>  
  
 <span data-ttu-id="0feb6-114">기본값은 2입니다.</span><span class="sxs-lookup"><span data-stu-id="0feb6-114">The default value is 2.</span></span>  
  
 <span data-ttu-id="0feb6-115">**보존 기간 단위**</span><span class="sxs-lookup"><span data-stu-id="0feb6-115">**Retention Period Units**</span></span>  
 <span data-ttu-id="0feb6-116">보존 기간 값의 단위를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0feb6-116">Specifies the units for the Retention Period value.</span></span> <span data-ttu-id="0feb6-117">**일**, **시간**또는 **분**을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0feb6-117">You can select **Days**, **Hours**, or **Minutes**.</span></span> <span data-ttu-id="0feb6-118">기본값은 **일**입니다.</span><span class="sxs-lookup"><span data-stu-id="0feb6-118">The default value is **Days**.</span></span>  
  
 <span data-ttu-id="0feb6-119">최소 보존 기간은 1분입니다.</span><span class="sxs-lookup"><span data-stu-id="0feb6-119">The minimum retention period is 1 minute.</span></span> <span data-ttu-id="0feb6-120">최대 보존 기간은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0feb6-120">There is no maximum retention period.</span></span>  
  
 <span data-ttu-id="0feb6-121">**자동 정리**</span><span class="sxs-lookup"><span data-stu-id="0feb6-121">**Auto Clean-Up**</span></span>  
 <span data-ttu-id="0feb6-122">지정된 보존 기간 후에 변경 내용 추적 정보가 자동으로 제거되는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0feb6-122">Indicates whether change tracking information is automatically removed after the specified retention period.</span></span>  
  
 <span data-ttu-id="0feb6-123">**자동 정리** 를 설정하면 이전의 모든 사용자 지정 보존 기간이 기본 보존 기간인 2일로 다시 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="0feb6-123">Enabling **Auto Clean-Up** resets any previous custom retention period to the default retention period of 2 days.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0feb6-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0feb6-124">See Also</span></span>  
 <span data-ttu-id="0feb6-125">[ALTER DATABASE &#40;Transact-SQL &#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0feb6-125">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 [<span data-ttu-id="0feb6-126">CREATE DATABASE&#40;SQL Server Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0feb6-126">CREATE DATABASE &#40;SQL Server Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-database-sql-server-transact-sql)  
  
  
