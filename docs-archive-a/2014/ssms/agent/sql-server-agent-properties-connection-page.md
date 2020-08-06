---
title: SQL Server 에이전트 속성(연결 탭) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.agent.connection.f1
ms.assetid: d6a677ff-60ad-47ba-a0cb-df4193b165e0
author: stevestein
ms.author: sstein
ms.openlocfilehash: ec9ae575f1ced510d95256d6827435e5b6ad89d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659775"
---
# <a name="sql-server-agent-properties-connection-page"></a><span data-ttu-id="4c63c-102">SQL Server 에이전트 속성(연결 탭)</span><span class="sxs-lookup"><span data-stu-id="4c63c-102">SQL Server Agent Properties (Connection Page)</span></span>
  <span data-ttu-id="4c63c-103">이 페이지를 사용 하 여 에이전트 서비스에서로의 연결 설정을 확인 하 고 수정할 수 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c63c-103">Use this page to view and modify the settings for the connection from the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="4c63c-104">옵션</span><span class="sxs-lookup"><span data-stu-id="4c63c-104">Options</span></span>  
 <span data-ttu-id="4c63c-105">**로컬 호스트 서버 별칭**</span><span class="sxs-lookup"><span data-stu-id="4c63c-105">**Alias local host server**</span></span>  
 <span data-ttu-id="4c63c-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 로컬 인스턴스에 연결하는 데 사용할 별칭을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4c63c-106">Specifies the alias to use to connect to the local instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="4c63c-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트에 기본 연결 옵션을 사용할 수 없는 경우 인스턴스에 대한 별칭을 정의한 후 여기에서 해당 별칭을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4c63c-107">If you cannot use the default connection options for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, define an alias for the instance and specify the alias here.</span></span>  
  
 <span data-ttu-id="4c63c-108">**Windows 인증 사용**</span><span class="sxs-lookup"><span data-stu-id="4c63c-108">**Use Windows Authentication**</span></span>  
 <span data-ttu-id="4c63c-109">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 인증을 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스 연결에 사용하는 인증 방법으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="4c63c-109">Sets [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Authentication as the authentication method used to connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="4c63c-110">에이전트가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스 실행에 사용되는 계정으로 연결하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4c63c-110">Agent connects as the account that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service runs as.</span></span>  
  
 <span data-ttu-id="4c63c-111">**SQL Server 인증 사용**</span><span class="sxs-lookup"><span data-stu-id="4c63c-111">**Use SQL Server Authentication**</span></span>  
 <span data-ttu-id="4c63c-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스 연결에 사용하는 인증 방법으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="4c63c-112">Sets [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication as the authentication method used to connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="4c63c-113">인증은 이전 버전과의 호환성을 위해 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="4c63c-113">Authentication is provided for backward compatibility.</span></span> <span data-ttu-id="4c63c-114">보안 향상을 위해 가능하면 Windows 인증을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4c63c-114">For improved security, use Windows Authentication if possible.</span></span>  
  
 <span data-ttu-id="4c63c-115">**로그인**</span><span class="sxs-lookup"><span data-stu-id="4c63c-115">**Login**</span></span>  
 <span data-ttu-id="4c63c-116">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]연결에 사용할 로그인 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4c63c-116">Specifies the login name to use to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="4c63c-117">**암호**</span><span class="sxs-lookup"><span data-stu-id="4c63c-117">**Password**</span></span>  
 <span data-ttu-id="4c63c-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]연결에 사용할 암호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4c63c-118">Specifies the password to use to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
  
