---
title: SQLXML 관리 되는 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- .NET Framework [SQLXML], Managed Classes
- SQL Server .NET Data Provider
- Managed Classes [SQLXML], about managed classes
- providers [SQLXML], SQL Server .NET Data Provider
- data providers [SQLXML], SQL Server .NET Data Provider
- Managed Classes [SQLXML]
- XML [SQLXML]
- SQLXML Managed Classes
- providers [SQLXML], SQLXML Managed Classes
- data providers [SQLXML], SQLXML Managed Classes
- SQLXML, Managed Classes
ms.assetid: 73a5faeb-dabf-4895-acb5-a9651b646065
author: rothja
ms.author: jroth
ms.openlocfilehash: bb8d2d4f2d2fc512901e4ad37f0e46cf696b9475
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638617"
---
# <a name="sqlxml-managed-classes"></a><span data-ttu-id="c8bdb-102">SQLXML 관리되는 클래스</span><span class="sxs-lookup"><span data-stu-id="c8bdb-102">SQLXML Managed Classes</span></span>
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="c8bdb-103">SQLXML 관리되는 클래스는 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework 내에서 SQLXML 4.0의 기능을 공개합니다.</span><span class="sxs-lookup"><span data-stu-id="c8bdb-103">SQLXML Managed Classes exposes the functionality of SQLXML 4.0 inside the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework.</span></span> <span data-ttu-id="c8bdb-104">SQLXML 관리되는 클래스를 사용하면 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에서 XML 데이터에 액세스하고, .NET Framework 환경으로 데이터를 가져오며, 데이터를 처리하고, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에 업데이트를 DiffGram으로 다시 보내 적용하는 C# 애플리케이션을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8bdb-104">With SQLXML Managed Classes, you can write a C# application to access XML data from an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], bring the data into the .NET Framework environment, process the data, and send the updates back to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] as a DiffGram to apply the updates.</span></span> <span data-ttu-id="c8bdb-105">SQLXML 관리되는 클래스를 사용하여 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 데이터베이스로 업데이트를 적용할 때는 매핑 스키마를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8bdb-105">You must use a mapping schema when applying updates to a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database using SQLXML Managed Classes.</span></span> <span data-ttu-id="c8bdb-106">작업 예제는 [.Net 환경에서 SQLXML 기능에 액세스](accessing-sqlxml-functionality-in-the-net-environment.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c8bdb-106">For a working sample, see [Accessing SQLXML Functionality in the .NET Environment](accessing-sqlxml-functionality-in-the-net-environment.md).</span></span>  
  
 <span data-ttu-id="c8bdb-107">SQLXML 4.0에서 SQLXML 관리되는 클래스를 사용하려면 Microsoft Visual Studio를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8bdb-107">To use the SQLXML Managed Classes with SQLXML 4.0, you must install Microsoft Visual Studio.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c8bdb-108">.NET Framework에는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .NET 데이터 공급자가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8bdb-108">The .NET Framework includes the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .NET Data Provider.</span></span> <span data-ttu-id="c8bdb-109">이 공급자는 .NET 환경에서 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에 액세스하는 데 사용할 수 있지만 기존 SQL 쿼리(FOR XML 쿼리를 제외한 관계형 데이터베이스 쿼리)만 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8bdb-109">This provider can be used to access [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] from the .NET environment; however, it can handle only traditional SQL queries (that is, relational database queries with the exception of FOR XML queries).</span></span> <span data-ttu-id="c8bdb-110">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서는 XML 템플릿 또는 서버 쪽 XPath 쿼리를 실행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c8bdb-110">You cannot execute XML templates or the server-side XPath queries in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c8bdb-111">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="c8bdb-111">In This Section</span></span>  
 [<span data-ttu-id="c8bdb-112">SQLXML 관리되는 클래스 개체 모델</span><span class="sxs-lookup"><span data-stu-id="c8bdb-112">SQLXML Managed Classes Object Model</span></span>](../../../database-engine/dev-guide/sqlxml-managed-classes-object-model.md)  
 <span data-ttu-id="c8bdb-113">SQLXML 관리되는 클래스 및 이러한 클래스의 속성과 메서드에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c8bdb-113">Documents SQLXML Managed Classes and their properties and methods.</span></span>  
  
 [<span data-ttu-id="c8bdb-114">SQLXML 관리되는 클래스 사용</span><span class="sxs-lookup"><span data-stu-id="c8bdb-114">Using the SQLXML Managed Classes</span></span>](sqlxml-4-0-net-framework-support-managed-classes.md)  
 <span data-ttu-id="c8bdb-115">SQLXML 관리되는 클래스를 사용하는 예를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c8bdb-115">Provides examples of using SQLXML Managed Classes.</span></span>  
  
  
