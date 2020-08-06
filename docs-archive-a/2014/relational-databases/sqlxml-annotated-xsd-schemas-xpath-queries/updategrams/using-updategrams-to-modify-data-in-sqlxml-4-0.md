---
title: Updategrams을 사용 하 여 SQLXML 4.0에서 데이터 수정 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXML, updategrams
- data insertions [SQLXML]
- data deletions [SQLXML]
- updating data [SQLXML]
- modifying data [SQLXML]
- OPENXML function
- updategrams [SQLXML]
- database modifications [SQLXML]
- data updates [SQLXML]
- modifying databases
- data modifications [SQLXML]
- deleting data
- inserting data
ms.assetid: b8b3b892-cb73-41d0-b945-bce148d81d9b
author: rothja
ms.author: jroth
ms.openlocfilehash: a4a2397668ed08df91377cc35dea22fd52788580
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652728"
---
# <a name="using-updategrams-to-modify-data-in-sqlxml-40"></a><span data-ttu-id="64180-102">SQLXML 4.0에서 updategram을 사용하여 데이터 수정</span><span class="sxs-lookup"><span data-stu-id="64180-102">Using Updategrams to Modify Data in SQLXML 4.0</span></span>
  <span data-ttu-id="64180-103">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] UPDATEGRAM 또는 OPENXML 함수를 사용 하 여 기존 XML 문서에서 데이터베이스를 수정 (삽입, 업데이트 또는 삭제) 할 수 있습니다 [!INCLUDE[tsql](../../../includes/tsql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="64180-103">You can modify (insert, update, or delete) a database in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] from an existing XML document by using an updategram or the OPENXML [!INCLUDE[tsql](../../../includes/tsql-md.md)] function.</span></span>  
  
 <span data-ttu-id="64180-104">이 섹션에서는 updategram에 대해 설명하고 updategram 사용 예를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="64180-104">This section provides information about updategrams and examples of their usage.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="64180-105">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="64180-105">In This Section</span></span>  
 [<span data-ttu-id="64180-106">Updategrams &#40;SQLXML 4.0&#41;소개</span><span class="sxs-lookup"><span data-stu-id="64180-106">Introduction to Updategrams &#40;SQLXML 4.0&#41;</span></span>](introduction-to-updategrams-sqlxml-4-0.md)  
 <span data-ttu-id="64180-107">Updategram에 대한 기본 정보 및 예를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="64180-107">Provides basic information and examples of updategrams.</span></span>  
  
 [<span data-ttu-id="64180-108">Updategram &#40;SQLXML 4.0&#41;에서 주석이 추가 된 매핑 스키마 지정</span><span class="sxs-lookup"><span data-stu-id="64180-108">Specifying an Annotated Mapping Schema in an Updategram &#40;SQLXML 4.0&#41;</span></span>](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md)  
 <span data-ttu-id="64180-109">Updategram의 주석이 추가된 매핑 스키마에 대해 설명하고 이에 대한 예를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="64180-109">Explains and provides examples of annotated mapping schemas in updategrams.</span></span>  
  
 [<span data-ttu-id="64180-110">SQLXML 4.0 &#40;NULL 처리&#41;</span><span class="sxs-lookup"><span data-stu-id="64180-110">NULL Handling &#40;SQLXML 4.0&#41;</span></span>](null-handling-sqlxml-4-0.md)  
 <span data-ttu-id="64180-111">요소 및 특성 값에 NULL을 지정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="64180-111">Describes how to specify NULL for element and attribute values.</span></span>  
  
 [<span data-ttu-id="64180-112">XML Updategrams &#40;SQLXML 4.0&#41;를 사용 하 여 데이터 삽입</span><span class="sxs-lookup"><span data-stu-id="64180-112">Inserting Data Using XML Updategrams &#40;SQLXML 4.0&#41;</span></span>](inserting-data-using-xml-updategrams-sqlxml-4-0.md)  
 <span data-ttu-id="64180-113">Updategram을 사용하여 데이터를 삽입하는 방법을 설명하고 이에 대한 예를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="64180-113">Describes and provides examples of using updategrams to insert data.</span></span>  
  
 [<span data-ttu-id="64180-114">XML Updategrams &#40;SQLXML 4.0&#41;를 사용 하 여 데이터 삭제</span><span class="sxs-lookup"><span data-stu-id="64180-114">Deleting Data Using XML Updategrams &#40;SQLXML 4.0&#41;</span></span>](deleting-data-using-xml-updategrams-sqlxml-4-0.md)  
 <span data-ttu-id="64180-115">Updategram을 사용하여 데이터를 삭제하는 방법을 설명하고 이에 대한 예를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="64180-115">Describes and provides examples of using updategrams to delete data.</span></span>  
  
 [<span data-ttu-id="64180-116">XML Updategrams &#40;SQLXML 4.0&#41;를 사용 하 여 데이터 업데이트</span><span class="sxs-lookup"><span data-stu-id="64180-116">Updating Data Using XML Updategrams &#40;SQLXML 4.0&#41;</span></span>](updating-data-using-xml-updategrams-sqlxml-4-0.md)  
 <span data-ttu-id="64180-117">Updategram을 사용하여 기존 데이터를 수정하는 방법을 설명하고 이에 대한 예를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="64180-117">Describes and provides examples of using updategrams to modify existing data.</span></span>  
  
 [<span data-ttu-id="64180-118">Updategrams &#40;SQLXML 4.0&#41;에 매개 변수 전달</span><span class="sxs-lookup"><span data-stu-id="64180-118">Passing Parameters to Updategrams &#40;SQLXML 4.0&#41;</span></span>](passing-parameters-to-updategrams-sqlxml-4-0.md)  
 <span data-ttu-id="64180-119">매개 변수를 updategram에 전달하는 방법을 설명하고 이에 대한 예를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="64180-119">Describes and provides examples of passing parameters to updategrams.</span></span>  
  
 [<span data-ttu-id="64180-120">Updategrams에서 데이터베이스 동시성 문제 처리 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="64180-120">Handling Database Concurrency Issues in Updategrams &#40;SQLXML 4.0&#41;</span></span>](handling-database-concurrency-issues-in-updategrams-sqlxml-4-0.md)  
 <span data-ttu-id="64180-121">Updategram에서 동시성 문제를 처리하는 데 사용할 수 있는 다양한 수준의 보호에 대해 설명하고 이에 대한 예를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="64180-121">Describes the various levels of protection possible for handling concurrency issues in updategrams, and provides examples.</span></span>  
  
 [<span data-ttu-id="64180-122">Updategram 샘플 응용 프로그램 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="64180-122">Updategram Sample Applications &#40;SQLXML 4.0&#41;</span></span>](../../../database-engine/dev-guide/updategram-sample-applications-sqlxml-4-0.md)  
 <span data-ttu-id="64180-123">Updategram을 사용하는 예제 애플리케이션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="64180-123">Provides sample applications that use updategrams.</span></span>  
  
 [<span data-ttu-id="64180-124">XML Updategrams &#40;SQLXML 4.0에 대 한 지침 및 제한 사항&#41;</span><span class="sxs-lookup"><span data-stu-id="64180-124">Guidelines and Limitations of XML Updategrams &#40;SQLXML 4.0&#41;</span></span>](guidelines-and-limitations-of-xml-updategrams-sqlxml-4-0.md)  
 <span data-ttu-id="64180-125">Updategram 사용 시 주의해야 할 사항에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="64180-125">Lists some things to remember when working with updategrams.</span></span>  
  
  
