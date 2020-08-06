---
title: 자동 관리 캐싱 (차원) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- dimensions [Analysis Services], proactive caching
- proactive caching [Analysis Services]
ms.assetid: 7d57fe93-6e5f-4a50-844f-dd2bbdbb94a5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 50c723d46b6c51fae0ccc227b5e58cf96f72c7b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647303"
---
# <a name="proactive-caching-dimensions"></a><span data-ttu-id="7db98-102">자동 관리 캐싱(차원)</span><span class="sxs-lookup"><span data-stu-id="7db98-102">Proactive Caching (Dimensions)</span></span>
  <span data-ttu-id="7db98-103">자동 관리 캐싱은 OLAP 개체에 자동 MOLAP 캐시 생성 및 관리 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7db98-103">Proactive caching provides automatic MOLAP cache creation and management for OLAP objects.</span></span> <span data-ttu-id="7db98-104">큐브는 데이터베이스로부터 알림을 수신하는 즉시 데이터베이스에 있는 데이터의 변경 내용을 통합합니다.</span><span class="sxs-lookup"><span data-stu-id="7db98-104">The cubes immediately incorporate changes that are made to the data in the database, based upon notifications received from the database.</span></span> <span data-ttu-id="7db98-105">자동 관리 캐싱의 목표는 ROLAP에서 제공하는 즉시성과 관리 용이성을 유지하면서 기존 MOLAP의 성능을 제공하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="7db98-105">The goal of proactive caching is to provide the performance of traditional MOLAP, while retaining the immediacy and ease of management offered by ROLAP.</span></span>  
  
 <span data-ttu-id="7db98-106">단순 <xref:Microsoft.AnalysisServices.ProactiveCaching> 개체는 타이밍 사양과 테이블 알림으로 구성되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7db98-106">A simple <xref:Microsoft.AnalysisServices.ProactiveCaching> object is composed of: timing specification, and table notification.</span></span> <span data-ttu-id="7db98-107">타이밍 사양은 변경 알림을 수신한 후 캐시를 업데이트하는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="7db98-107">The timing specification defines the timeframe for updating the cache after a change notification has been received.</span></span> <span data-ttu-id="7db98-108">테이블 알림은 데이터 테이블과 <xref:Microsoft.AnalysisServices.ProactiveCaching> 개체 간의 알림 스키마를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="7db98-108">The table notification defines the notification schema between the data table and the <xref:Microsoft.AnalysisServices.ProactiveCaching> object.</span></span>  
  
  
