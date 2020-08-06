---
title: CLR 통합의 아키텍처 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- common language runtime [SQL Server], architecture
- architecture [CLR integration]
ms.assetid: 05e4b872-3d21-46de-b4d5-739b5f2a0cf9
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: bb32e2c7f5eb2079146a2fee64af2e2dbc1d3356
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648543"
---
# <a name="architecture-of-clr-integration"></a><span data-ttu-id="4f3e6-102">CLR 통합 아키텍처</span><span class="sxs-lookup"><span data-stu-id="4f3e6-102">Architecture of CLR Integration</span></span>
  <span data-ttu-id="4f3e6-103">.NET Framework CLR(공용 언어 런타임)과 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 통합을 사용하면 데이터베이스 프로그래머가 Visual C#, Visual Basic .NET, 및 Visual C++와 같은 언어를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f3e6-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] integration with the .NET Framework common language runtime (CLR) enables database programmers to use languages such as Visual C#, Visual Basic .NET, and Visual C++.</span></span> <span data-ttu-id="4f3e6-104">프로그래머가 이러한 언어를 사용하여 작성할 수 있는 비즈니스 논리의 종류에는 함수, 저장 프로시저, 트리거, 데이터 형식, 집계 등이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f3e6-104">Functions, stored procedures, triggers, data types, and aggregates are among the kinds of business logic that programmers can write with these languages.</span></span>  
  
 <span data-ttu-id="4f3e6-105">이 섹션에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 내의 CLR 통합 아키텍처와 이러한 아키텍처에서 사용자 코드를 실행할 안전하고 확장 가능하며 효율적인 보안 환경을 제공하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4f3e6-105">This section describes the architecture of CLR integration inside [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and how this architecture provides a safe, scalable, secure, and efficient environment to run user code.</span></span>  
  
 <span data-ttu-id="4f3e6-106">다음 표에서는 이 섹션에서 다루는 항목을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="4f3e6-106">The following table lists the topics in this section.</span></span>  
  
 [<span data-ttu-id="4f3e6-107">CLR 호스팅 환경</span><span class="sxs-lookup"><span data-stu-id="4f3e6-107">CLR Hosted Environment</span></span>](../../relational-databases/clr-integration/clr-integration-architecture-clr-hosted-environment.md)  
 <span data-ttu-id="4f3e6-108">CLR 통합의 아키텍처 설계 목표, 메커니즘 및 이점에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4f3e6-108">Discusses architectural design goals, mechanisms, and benefits of CLR integration.</span></span>  
  
 [<span data-ttu-id="4f3e6-109">통합된 CLR의 성능</span><span class="sxs-lookup"><span data-stu-id="4f3e6-109">Performance of CLR Integration</span></span>](../../relational-databases/clr-integration/clr-integration-architecture-performance.md)  
 <span data-ttu-id="4f3e6-110">CLR 통합 아키텍처의 성능 고려 사항을 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="4f3e6-110">Covers performance considerations of the CLR integration architecture.</span></span>  
  
  
