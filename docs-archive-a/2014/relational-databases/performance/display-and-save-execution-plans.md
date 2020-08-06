---
title: 실행 계획 표시 및 저장 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Showplan results
- execution plans [SQL Server]
- queries [SQL Server], tuning
- execution plans [SQL Server], how-to topics
- SQL Server Management Studio [SQL Server], execution plans
- tuning queries [SQL Server]
ms.assetid: bcd6f094-c613-4835-ae19-4caaadb4bb17
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e236ed2a298bc8fc9a829948a864f6f5c27a2ba2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730551"
---
# <a name="display-and-save-execution-plans"></a><span data-ttu-id="97100-102">실행 계획 표시 및 저장</span><span class="sxs-lookup"><span data-stu-id="97100-102">Display and Save Execution Plans</span></span>
  <span data-ttu-id="97100-103">이 섹션에서는 실행 계획을 표시하는 방법과 Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 사용하여 실행 계획을 XML 형식의 파일로 저장하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="97100-103">This section explains how to display execution plans and how to save execution plans to a file in XML format by using Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="97100-104">실행 계획은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 쿼리 최적화 프로그램에서 선택한 데이터 검색 방법을 그래픽으로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="97100-104">Execution plans graphically display the data retrieval methods chosen by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] query optimizer.</span></span> <span data-ttu-id="97100-105">실행 계획은 SET SHOWPLAN_ALL 또는 SET SHOWPLAN_TEXT 문으로 생성되는 테이블 형식이 아닌 아이콘으로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 특정 문과 쿼리 실행 비용을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="97100-105">Execution plans represent the execution cost of specific statements and queries in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using icons rather than the tabular representation produced by the SET SHOWPLAN_ALL or SET SHOWPLAN_TEXT statements.</span></span> <span data-ttu-id="97100-106">이러한 그래픽 표시는 쿼리의 성능 특성을 이해하는 데 매우 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="97100-106">This graphical approach is very useful for understanding the performance characteristics of a query.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="97100-107">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="97100-107">In This Section</span></span>  
  
-   [<span data-ttu-id="97100-108">예상 실행 계획 표시</span><span class="sxs-lookup"><span data-stu-id="97100-108">Display the Estimated Execution Plan</span></span>](display-the-estimated-execution-plan.md)  
  
-   [<span data-ttu-id="97100-109">실제 실행 계획 표시</span><span class="sxs-lookup"><span data-stu-id="97100-109">Display an Actual Execution Plan</span></span>](display-an-actual-execution-plan.md)  
  
-   [<span data-ttu-id="97100-110">XML 형식으로 실행 계획 저장</span><span class="sxs-lookup"><span data-stu-id="97100-110">Save an Execution Plan in XML Format</span></span>](save-an-execution-plan-in-xml-format.md)  
  
  
