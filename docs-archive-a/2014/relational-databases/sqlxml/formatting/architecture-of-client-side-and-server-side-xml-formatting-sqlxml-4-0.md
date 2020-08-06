---
title: 클라이언트 쪽 및 서버 쪽 XML 서식 지정 아키텍처 (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- providers [SQLXML], XML formatting architecture
- SQLOLEDB provider
- client-side XML formatting
- data providers [SQLXML], XML formatting architecture
- SQLNCLI, XML
- server-side XML formatting
- SQL Server Native Client, XML
- SQLXMLOLEDB Provider, XML formatting architecture
ms.assetid: 52440d9e-89fd-4c15-a008-a1ea99f41387
author: rothja
ms.author: jroth
ms.openlocfilehash: ae1a9c60a7a7966f4eff2a08b4557487f5aec58c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652712"
---
# <a name="architecture-of-client-side-and-server-side-xml-formatting-sqlxml-40"></a><span data-ttu-id="a63e3-102">클라이언트 쪽 및 서버 쪽 XML 서식 지정 아키텍처(SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="a63e3-102">Architecture of Client-side and Server-side XML Formatting (SQLXML 4.0)</span></span>
  <span data-ttu-id="a63e3-103">다음 그림에서는 서버 쪽 XML 서식 지정 아키텍처를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a63e3-103">The following illustration shows the architecture of XML formatting on the server side.</span></span>  
  
 <span data-ttu-id="a63e3-104">![서버 쪽 XML 서식 지정 아키텍처](../../../database-engine/dev-guide/media/serversidexml.gif "서버 쪽 XML 서식 지정 아키텍처")</span><span class="sxs-lookup"><span data-stu-id="a63e3-104">![Architecture of XML formatting on the server side.](../../../database-engine/dev-guide/media/serversidexml.gif "Architecture of XML formatting on the server side.")</span></span>  
  
 <span data-ttu-id="a63e3-105">이 예에서는 클라이언트에서 지정한 명령이 서버로 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="a63e3-105">In this example, the command that is specified on the client is sent to the server.</span></span> <span data-ttu-id="a63e3-106">서버는 XML 문서를 생성하여 클라이언트로 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="a63e3-106">The server produces an XML document and returns it to the client.</span></span> <span data-ttu-id="a63e3-107">이 경우 서버에는의 인스턴스가 있습니다 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="a63e3-107">In this case, the server has an instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a63e3-108">서버 쪽 XML 서식 지정을 사용하면 SQLXMLOLEDB 공급자나 SQLOLEDB 공급자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a63e3-108">With server-side XML formatting, you can use either the SQLXMLOLEDB provider or the SQLOLEDB provider.</span></span>  <span data-ttu-id="a63e3-109">SQLXMLOLEDB 공급자는 SQLXML 4.0에 포함된 Sqlxml4.dll을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a63e3-109">The SQLXMLOLEDB provider uses Sqlxml4.dll, which is included in SQLXML 4.0.</span></span> <span data-ttu-id="a63e3-110">SQLOLEDB 공급자를 사용하면 기본적으로 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows 또는 MDAC(Microsoft Data Access Components) 2.6 이상 버전에 포함된 Sqlxmlx.dll에서 제공되는 SQLXML 기능을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a63e3-110">When you use the SQLOLEDB provider, by default you get the SQLXML functionality provided by Sqlxmlx.dll, which is included with [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows or in Microsoft Data Access Components (MDAC) 2.6 or later.</span></span> <span data-ttu-id="a63e3-111">SQLOLEDB와 함께 Sqlxml4.dll를 사용 하려면 SQLOLEDB 연결 개체에서 SQLXML 버전 속성을 "SQLXML. 4.0"으로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a63e3-111">To use Sqlxml4.dll with SQLOLEDB, you must set the SQLXML Version property to "SQLXML.4.0" on the SQLOLEDB Connection object.</span></span> <span data-ttu-id="a63e3-112">두 경우 모두, 서버는 XML 문서를 생성하여 클라이언트로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="a63e3-112">In either case, the server produces the XML document and sends it to the client.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a63e3-113">XPath 쿼리 및 Updategram은 클라이언트에서 구문 분석됩니다.</span><span class="sxs-lookup"><span data-stu-id="a63e3-113">XPath queries and updategrams are parsed on the client.</span></span> <span data-ttu-id="a63e3-114">SQLXML 4.0의 XPath 템플릿이나 Updategram 기능을 가져오려면 Sqlxml4.dll을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a63e3-114">To get the XPath template or updategram functionality in SQLXML 4.0, use Sqlxml4.dll.</span></span>  
  
 <span data-ttu-id="a63e3-115">다음 그림에서는 클라이언트 쪽 XML 서식 지정 아키텍처를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a63e3-115">The following illustration shows the architecture of XML formatting on the client side.</span></span>  
  
 <span data-ttu-id="a63e3-116">![클라이언트 쪽의 XML 서식 지정 아키텍처](../../../database-engine/dev-guide/media/clientsidexml.gif "클라이언트 쪽의 XML 서식 지정 아키텍처")</span><span class="sxs-lookup"><span data-stu-id="a63e3-116">![Architecture of XML formatting on the client side.](../../../database-engine/dev-guide/media/clientsidexml.gif "Architecture of XML formatting on the client side.")</span></span>  
  
 <span data-ttu-id="a63e3-117">이 예에서 클라이언트는 SQLXMLOLEDB 공급자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a63e3-117">In this example, the client uses the SQLXMLOLEDB provider.</span></span> <span data-ttu-id="a63e3-118">연결 문자열에서 Data Provider 속성은 SQLOLEDB로 설정 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a63e3-118">In the connection string, the Data Provider property must be set to SQLOLEDB.</span></span> <span data-ttu-id="a63e3-119">(SQLXML 4.0에서 유일 하 게 허용 되는 값입니다.) 클라이언트에서 실행 되는 명령이 서버에 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a63e3-119">(This is the only value accepted in SQLXML 4.0.) The command that is executed on the client is sent to the server.</span></span> <span data-ttu-id="a63e3-120">서버에서 생성된 행 집합은 클라이언트로 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="a63e3-120">The rowset that is generated on the server is sent to the client.</span></span> <span data-ttu-id="a63e3-121">행 집합의 XML 문서 서식은 클라이언트에서 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="a63e3-121">The formatting of the XML document from the rowset is performed on the client.</span></span>  
  
 <span data-ttu-id="a63e3-122">SQLXML 4.0에서는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client(SQLNCLI11) 또는 SQLOLEDB 공급자를 데이터 공급자로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a63e3-122">In SQLXML 4.0, either the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (SQLNCLI11) or the SQLOLEDB provider can be used as the data provider.</span></span> <span data-ttu-id="a63e3-123">잠재적으로 모든 데이터 원본에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a63e3-123">You can potentially access any data source.</span></span> <span data-ttu-id="a63e3-124">쿼리에서 단일 행 집합을 반환하는 경우 클라이언트에 XML 변환을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a63e3-124">As long as the query returns a single rowset, the XML transformation can be applied on the client.</span></span>  
  
  
