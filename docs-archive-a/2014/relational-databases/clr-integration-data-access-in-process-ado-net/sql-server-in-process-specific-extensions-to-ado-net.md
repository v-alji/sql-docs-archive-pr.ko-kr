---
title: ADO.NET에 대 한 In-process 고유의 확장을 SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- data access [CLR integration]
- ADO.NET [CLR integration]
- common language runtime [SQL Server], ADO.NET
- database objects [CLR integration], in-process extensions
- in-process data access providers [CLR integration]
- extensions [CLR integration]
ms.assetid: 781b812e-eb14-472a-85fa-aa4cdb929bee
author: rothja
ms.author: jroth
ms.openlocfilehash: 37d8aedc1d8f93739c2e9386665adfc67b43e312
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660636"
---
# <a name="sql-server-in-process-specific-extensions-to-adonet"></a><span data-ttu-id="0c67c-102">ADO.NET에 대한 SQL Server In-Process 전용 확장</span><span class="sxs-lookup"><span data-stu-id="0c67c-102">SQL Server In-Process Specific Extensions to ADO.NET</span></span>
  <span data-ttu-id="0c67c-103">ADO.NET과 관련하여 In-Process에 사용하기 위해 특별히 고안된 네 가지 주요 기능 확장이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c67c-103">There are four main functional extensions to ADO.NET that are specifically for in-process use.</span></span> <span data-ttu-id="0c67c-104">다음 항목에서는 이러한 확장에 대해 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0c67c-104">The following topics will cover these extensions in detail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0c67c-105">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="0c67c-105">In This Section</span></span>  
 [<span data-ttu-id="0c67c-106">SqlContext 개체</span><span class="sxs-lookup"><span data-stu-id="0c67c-106">SqlContext Object</span></span>](sqlcontext-object.md)  
 <span data-ttu-id="0c67c-107">이 클래스는 관리 코드를 In-Process로 실행하는 SQL Server 루틴 호출자의 컨텍스트를 추상화하여 다른 확장에 대한 액세스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0c67c-107">This class provides access to the other extensions by abstracting the context of a caller of a SQL Server routine that executes managed code in-process.</span></span>  
  
 [<span data-ttu-id="0c67c-108">SqlPipe 개체</span><span class="sxs-lookup"><span data-stu-id="0c67c-108">SqlPipe Object</span></span>](sqlpipe-object.md)  
 <span data-ttu-id="0c67c-109">이 클래스에는 테이블 형식 결과 및 메시지를 클라이언트로 보내는 루틴이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c67c-109">This class contains routines to send tabular results and messages to the client.</span></span>  
  
 [<span data-ttu-id="0c67c-110">SqlTriggerContext 개체</span><span class="sxs-lookup"><span data-stu-id="0c67c-110">SqlTriggerContext Object</span></span>](sqltriggercontext-object.md)  
 <span data-ttu-id="0c67c-111">이 클래스는 트리거가 실행되는 컨텍스트에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0c67c-111">This class provides information on the context in which a trigger is run.</span></span>  
  
 [<span data-ttu-id="0c67c-112">SqlDataRecord 개체</span><span class="sxs-lookup"><span data-stu-id="0c67c-112">SqlDataRecord Object</span></span>](sqldatarecord-object.md)  
 <span data-ttu-id="0c67c-113">SqlDataRecord 클래스는 단일 데이터 행과 이와 관련된 메타데이터를 나타내며, 저장 프로시저는 이를 사용하여 사용자 지정 결과 집합을 클라이언트에 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c67c-113">The SqlDataRecord class represents a single row of data, along with its related metadata, and allows stored procedures to return custom result sets to the client.</span></span>  
  
  
